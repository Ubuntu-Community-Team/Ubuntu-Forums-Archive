---
title: "autofs auto.smb not working at all"
date: 2016-06-22
forum: Networking &amp; Wireless
---

### Post by xen3 on 2016-06-22
I have no clue what is wrong, but the autofs package is supposed to open the [COLOR=#0000cd]auto.smb[/COLOR] script when referenced, and it is not doing so.

[COLOR=#0000cd][/COLOR]I have tried to achieve the example of "/cifs /etc/auto.smb --timeout=300" but nothing is happening at all.

The problem is that I don't know what is going on because the actual reading apparently is supposed to happen in the kernel module (autofs.ko) and I don't really know how to trace it, without reading the source, in any case.

A command is executed by the daemon called "mount /etc/auto.smb /cifs -t autofs -o ......" as a form of a mount() system call. I cannot see the full parameters in strace, but apparently it is the module that is supposed to take the script and read it or execute it, but it is not doing so. Ostensibly it is not writing to a file I have it write to, to demonstrate if it works. Consequently, nothing ever happens to that /cifs directory.

So I have no freaking clue as to what is going on. This program was supposed to make my life easier, but I was suspicious from the get go, not only from its incomprehensible documentation.

But I've already spent hours trying to diagnose it and it is another example of "out of the box" solutions that just don't work in Linux.

I can verify the script actually works when given a network host as parameter. The script indeed generates a map file (on stdout). So I can run it manually and then just substitute that for the script, but that was not really the goal for it ;-). And, by the way, even the map file doesn't do anything.

The whole thing just doesn't work and also doesn't give any output. No directories are ever created (and they should). I just don't know what the hell is going on, but I don't really feel like wasting more time on this......

---

### Post by TheFu on 2016-06-22
I can hear your frustration and I'm sorry you feel that way.

If you'd actually like help, please post the **auto.master** and **auto.smb** config files inside code tags. Also telling us which packages were installed would be helpful too.  Or did I miss that information in the #1 post?

My mother always said ... "it helps to be polite when you need help from a stranger."  Coming into our home and calling our baby ugly isn't actually polite.  You haven't realized this yet, but some really smart people created almost all the server programs. I find it best to assume I'm missing something/clueless when things don't work the way I thought they should. In 25 yrs, I've found about 5 bugs. Everything else was "user error" - my error.

---

### Post by xen3 on 2016-06-23
The auto.master is just the default, mostly.

```
#
# Sample auto.master file
# This is a 'master' automounter map and it has the following format:
# mount-point [map-type[,format]:]map [options]
# For details of the format look at auto.master(5).
#
#/misc  /etc/auto.misc
#
# NOTE: mounts done from a hosts map will be mounted with the
#   "nosuid" and "nodev" options unless the "suid" and "dev"
#   options are explicitly given.
#
#/net   -hosts
#
# Include /etc/auto.master.d/*.autofs
# The included files must conform to the format of this file.
#
+dir:/etc/auto.master.d
#
# Include central master map if it can be found using
# nsswitch sources.
#
# Note that if there are entries for /net or /misc (as
# above) in the included master map any keys that are the
# same will not be seen as the first read key seen takes
# precedence.
#
/cifs /etc/auto.smb

#+auto.master
```

I have tried both with and without the +auto.master. I don't really know what it does exactly.
```
#!/bin/bash

# This file must be executable to work! chmod 755!

# Automagically mount CIFS shares in the network, similar to
# what autofs -hosts does for NFS.

# Put a line like the following in /etc/auto.master:
# /cifs  /etc/auto.smb --timeout=300
# You'll be able to access Windows and Samba shares in your network
# under /cifs/host.domain/share

# "smbclient -L" is used to obtain a list of shares from the given host.
# In some environments, this requires valid credentials.

# This script knows 2 methods to obtain credentials:
# 1) if a credentials file (see mount.cifs(8)) is present
#    under /etc/creds/$key, use it.
# 2) Otherwise, try to find a usable kerberos credentials cache
#    for the uid of the user that was first to trigger the mount
#    and use that.
# If both methods fail, the script will try to obtain the list
# of shares anonymously.

get_krb5_cache() {
    cache=
    uid=${UID}
    for x in $(ls -d /run/user/$uid/krb5cc_* 2>/dev/null); do
        if [ -d "$x" ] && klist -s DIR:"$x"; then
        cache=DIR:$x
            return
        fi
    done
    if [ -f /tmp/krb5cc_$uid ] && klist -s /tmp/krb5cc_$uid; then
        cache=/tmp/krb5cc_$uid
        return
    fi
}

key="$1"
opts="-fstype=cifs"

echo "it is $1." >> /tmp/key

for P in /bin /sbin /usr/bin /usr/sbin
do
    if [ -x $P/smbclient ]
    then
        SMBCLIENT=$P/smbclient
        break
    fi
done

[ -x $SMBCLIENT ] || exit 1
creds=/etc/creds/$key
if [ -f "$creds" ]; then
    opts="$opts"',uid=$UID,gid=$GID,credentials='"$creds"
    smbopts="-A $creds"
else
    get_krb5_cache
    if [ -n "$cache" ]; then
        opts="$opts"',multiuser,cruid=$UID,sec=krb5i'
        smbopts="-k"
        export KRB5CCNAME=$cache
    else
        opts="$opts"',guest'
        smbopts="-N"
    fi
fi

$SMBCLIENT $smbopts -gL "$key" 2>/dev/null| awk -v "key=$key" -v "opts=$opts" -F '|' -- '
    BEGIN   { ORS=""; first=1 }
    /Disk/  {
          if (first)
            print opts; first=0
          dir = $2
          loc = $2
          # Enclose mount dir and location in quotes
          # Double quote "$" in location as it is special
          gsub(/\$$/, "\\$", loc);
          gsub(/\&/,"\\\\&",loc)
          print " \\\n\t \"/" dir "\"", "\"://" key "/" loc "\""
        }
    END     { if (!first) print "\n"; else exit 1 }

```

The only change to that file is this line:
```
echo "it is $1." >> /tmp/key
```

For some reason I have seen it invoked when $1 was "a" but I have no clue how, why or when.

I don't know what packages. I am running 16.04 and the only related stuff I have installed was "autofs"  and "smbclient" and "cifs-utils".

Here are perhaps some relevant lines. Contents of autofs package (binaries and such):

```
/etc/init.d/autofs/etc/init/autofs.conf
/usr/sbin/automount
/usr/lib/x86_64-linux-gnu/autofs/lookup_hosts.so
/usr/lib/x86_64-linux-gnu/autofs/mount_nfs.so
/usr/lib/x86_64-linux-gnu/autofs/mount_autofs.so
/usr/lib/x86_64-linux-gnu/autofs/mount_afs.so
/usr/lib/x86_64-linux-gnu/autofs/lookup_file.so
/usr/lib/x86_64-linux-gnu/autofs/parse_sun.so
/usr/lib/x86_64-linux-gnu/autofs/lookup_program.so
/usr/lib/x86_64-linux-gnu/autofs/mount_changer.so
/usr/lib/x86_64-linux-gnu/autofs/lookup_dir.so
/usr/lib/x86_64-linux-gnu/autofs/lookup_yp.so
/usr/lib/x86_64-linux-gnu/autofs/lookup_sss.so
/usr/lib/x86_64-linux-gnu/autofs/mount_generic.so
/usr/lib/x86_64-linux-gnu/autofs/mount_bind.so
/usr/lib/x86_64-linux-gnu/autofs/lookup_nisplus.so
/usr/lib/x86_64-linux-gnu/autofs/lookup_multi.so
/usr/lib/x86_64-linux-gnu/autofs/lookup_userhome.so
/usr/lib/x86_64-linux-gnu/autofs/mount_ext2.so
/usr/lib/x86_64-linux-gnu/autofs/parse_amd.so
/usr/lib/x86_64-linux-gnu/autofs/mount_nfs4.so
/usr/lib/x86_64-linux-gnu/autofs/lookup_files.so
/usr/lib/x86_64-linux-gnu/autofs/mount_ext3.so
/usr/lib/x86_64-linux-gnu/autofs/mount_ext4.so
/usr/lib/x86_64-linux-gnu/autofs/lookup_nis.so
```

Kernel module:
```
/lib/modules/4.4.0-24-generic/kernel/fs/autofs4/autofs4.ko
```

Cifs-utils:
```
/usr/bin/cifscreds
/usr/bin/setcifsacl
/usr/bin/getcifsacl
/usr/lib/x86_64-linux-gnu/cifs-utils/idmapwb.so
/usr/include/cifsidmap.h
/usr/sbin/cifs.upcall
/usr/sbin/cifs.idmap
/sbin/mount.cifs
/etc/request-key.d/cifs.idmap.conf
/etc/request-key.d/cifs.spnego.conf
```

Smbclient:
```
/usr/bin/rpcclient
/usr/bin/smbtar
/usr/bin/smbtree
/usr/bin/smbclient
/usr/bin/smbcacls
/usr/bin/smbcquotas
/usr/bin/smbspool_krb5_wrapper
/usr/bin/smbget
/usr/bin/smbspool
/usr/bin/cifsdd
```

(Excluding cups stuff).

> My mother always said ... "it helps to be polite when you need help from a stranger." Coming into our home and calling our baby ugly isn't actually polite. You haven't realized this yet, but some really smart people created almost all the server programs. I find it best to assume I'm missing something/clueless when things don't work the way I thought they should. In 25 yrs, I've found about 5 bugs. Everything else was "user error" - my error.

You know, that seems to juxtapose my intelligence with theirs, as if mine would be the lesser one.

My friends all teach at universities. One of my friends became a European "youth" champion in bridge about 4 years after starting playing it and has been a "world champion"  several times now. At the same time, some of them don't know how to bake an egg (or didn't know how to do that when I was living with them).

Became national youth champion in chess (her brother) under 14 several times, I believe, yet did the most incomprehensibly stupid things you cannot imagine, but would have you laughing your ass off ;-).

In general I have not come across anyone who was more intelligent than me apart from the fact that some (many) people are much better at doing certain things than I am. Yet I do not even feel like doing those things, you know. So the guy can play simultaneous chess matches blindly, and all of them have a memory of cards that dwarfs mine by a million times. What does it matter you know. Intelligence is not just being smart. It is also being wise.

What your mother said is in the books as well. Confucius has said such things as "The noble calms himself before he moves; he considers before he speaks; he strengthens his relations before he asks. By taking account of these three things, the noble is completely safe. When, on the other hand, one is unrestrained in ones movements, the people won't cooperate. When words are excited, they do not resonate with people. When one, not having made acquaintance, asks for something, people won't give it. When no one is with us, them who are against us, will come to do us harm." ;-). Or something of that kind, have to translate here.

User error, that's an antonym of bad design, in that sense. The pejorative word, the euphemism here, is that any form of bad operation of a machine (or program) is a "design feature". The thing crashes 20 times in a row? That's a *design feature*, be happy it exists! It is for your own good!.

By the way, Baloo constantly crashes, I don't know why ;-).

That might not be a server but at least it is a daemon. Well, it might be something of a server. Those very smart people are influenced by other people who might not be so very smart. Even the best of people have a hard time getting the work done that they want, if they constantly have to deal with other people who have requests of them. Design in Linux is rarely a choice made by a single person out of pure joy, but mostly, and morely so, something that "comes about" as many "important people" want to have their say.

This being completely and utterly dependent on the opinions of others is what makes the progress in Linux so slow, from my point of view. The more people have a say in something, the less the quality becomes. If you let everyone in the entire world have a say, you will have created something utterly without value.

Then, the intelligence becomes the intelligence of the system, and no longer that of a single person. And if the system promotes bad design choice, bad design choice it is.

On forums such as these, the atmosphere is much better than in some places. But in general. People are not very nice. People seem to revel in your misery. People seem to enjoy stuff being too hard to achieve. People seem to take pleasure in stuff being extremely hard. Really. User error can only happen in the space of the allowance of such error. The more something is neatly organized, as said before, the less prone you are to doing anything wrong.

Life is also a matter of ensuring you don't end up in dangerous situations where you *can* make a serious error.

In any case, I've mostly given up on getting help from Linux people. I almost never ask anything on IRC, because they first want a written and signed treatise on WHY you want to do a certain thing before they give you some information on how to do it. A computer won't complain. Google won't complain. "grep -r" is not going to ask me why I want to do it. It will just do it.

Being dependent on people who are in most cases unwilling to help is not a good thing.

When I use a computer, I don't have to negotiate whether the reasons for doing a certain thing are good. I won't have to survive interviews as to why I want to do something.

I just run into the fact that so much software is so badly written and has such bad user interfaces ;-).

Many man pages are written as a form of design specification, with all the rationale and all the definitions that go with the thing. But a fundamental design document is not what you are looking for when you open a man page. Some of them provide zero examples on how to use it. They seem to, on purpose, want to push you to search on.

I'm usually just hunting for examples because an example is worth a thousand words. And they are so rarely there.

There's usually a terrible amount of bad defaults, that are then excused by saying that everyone wants something else.

"You can't please everyone", they then say.

(Maybe if you tried it would work out much better than now that you don't even try).

So basically my current day experience is that I get no help, or people are so unwelcoming that it is much faster trying to find it with existing resources, because then you won't have to wait for other people to do the right thing. People are a huge disappointment to me really..........

(Just today read an article by a Microsoft programmer on how performant the "Excel team" was because they had written their own C compiler and had so few dependencies anywhere that they outperformed any other team in the company in a consistent fashion). (Another guy said how the software with the least dependencies was the easiest to port and migrate and fix). He said literally, that if you are a very good programmer, or team of programmers, then most of what other people create and make is "bug-infested garbage". And I can''t agree more.

And I have no time to be polite, really ;-). Death is closing in on me, in a m....anner of speaking.

The venerable I Ching also says: A casque of wine, a plate of rice as a gift, earthen saucers, Simply passed through the window, Is certainly without blame. And what it means is that ceremony ends when situations are urgent.

I simply have no more time to deal with people who are going to take their time not feeling any sense of urgency, as they ask questions that are not relevant and you have to be "polite" to answer their unhelpful questions. People who know less than you do, but who constantly feel they are in the position to help you. And if you then object to doing what they tell you, they become mad and consider you ungrateful.

Companies never behave that way, they come to the point as quickly as they can. But "volunteers" pretend that your time belongs to them.

I once filed a bug report for Firefox. I was then asked if I could spend my time mentoring someone who would then go and solve the problem with my help. It would probably take less time to solve it on my own. My bug description was so complete and so clear, that anyone should be able to reproduce it. They hadn't even tried yet, they just wanted me to help someone else help me. But apparently it was only seen as "education" for that other person.

Programming is something I grew up with, as well as you (Fu meister), perhaps. The whole idea that someone would need to teach me is ludicrous. For this reason I consider teaching it to someone else ludicrous as well, mostly. I won't teach people how to talk or breathe either, unless it is more advanced stuff.

Such ideas that people are incompetent and need "help" is beyond me.

---

