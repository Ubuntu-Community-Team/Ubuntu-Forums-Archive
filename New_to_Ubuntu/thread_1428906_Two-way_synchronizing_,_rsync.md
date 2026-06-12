---
title: "Two-way synchronizing , rsync?"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by markp1989 on 2010-03-13
im starting uni soon, and im looking for a way to automate syncronizationg of course work etc,

im gona have a work folder on my server (shared with nfs so i can work on my desktop)  and im gona have the same folder on my laptop.

im looking for a way that if i do work when im out, when i come home the changes will be copyed across to the work folder on the file server.

then if i work on the files on my desktop (accesing the work from server over nfs), for the changes to be syncronized to my laptop. 

i was thinking of drop box,but i  can see it using up aot of bandwith, and i dont really want to use a 3rd party person.

i use rsync+cron to back up my home dir on my laptop right now, is there away to run like a  2 way rsync so that the newest change is kept?

thanks markp1989

---

### Post by r-senior on 2010-03-13
Dropbox is fine in terms of bandwidth, you hardly notice it's there. I use it on dismal hotel wireless internet sometimes without problems. It's probably the neatest and easiest solution. Plus your files are backed up and versioned on the Dropbox website, and you can access your files from anywhere if you need to.

---

### Post by ugm6hr on 2010-03-14
Check out Unison: [http://homeserver.wikidot.com/unison](http://homeserver.wikidot.com/unison)

I only used it for a short trial and then went back to rsync, since I only worked on one computer.

---

### Post by yeats on 2010-03-14
Of course, there's always [Ubuntu One]("https://one.ubuntu.com/"), right? ;)

---

### Post by Penguin Guy on 2010-03-14
Just run two rsyncs at once: one downloading files, and one uploading files.

---

### Post by ugm6hr on 2010-03-14
> **Penguin Guy said:**
> Just run two rsyncs at once: one downloading files, and one uploading files.

I don't think that works.

Whichever runs first will update the other version - it will not maintain the most recently updated version.

---

### Post by Seq on 2010-03-14
I'll second unison. My desktop and server both share the same /home (via nfs), but I've used unison for a year to keep a local copy of /home on my laptop.

Unison does efficient delta transfers like rsync, but can do two-way. Furthermore, you actually get a list after the initial comparison showing you how things are going to go, including conflicts.

It works best if you are syncing between two computers using ssh, both with unison installed. That way each node builds its own list, which your client compares. If you are using unison to a mounted cifs or nfs share, you're still pulling everything across the network to compare it locally anyway, so you lose the benefit of transferring only deltas.

---

### Post by gare on 2010-04-04
> **ugm6hr said:**
> I don't think that works.

Whichever runs first will update the other version - it will not maintain the most recently updated version.


Hi -

using this switch would appear to prevent that issue:

```
-u, --update                skip files that are newer on the receiver
```

I found it while dissecting the rsync options used here:
[http://lists.freebsd.org/pipermail/freebsd-questions/2004-March/040093.htmal](http://lists.freebsd.org/pipermail/freebsd-questions/2004-March/040093.htmal)

> On Sun, Mar 14, 2004, Steven N. Fettig wrote:
>I have two workstations I use (one at home and one at work) connected 
>via a private DSL link that each have the directories /home/me.  I want 
>to run a cron job to sync the directories (bi-directionally).  Rsync 
>seems to work only in one direction (I know I could set up the script on 
>both machines), but I wanted to see if I could run the script on one 
>machine and simply copy new files over to the lacking machine or update 
>files via checksums (where a file has been updated on one machine and I 
>want that updated file to be copied over the old file on the other 
>machine).  I am not worried about the case where I might update a given 
>file on both machines at the same time - it doesn't happen.
>Any advice and scripts that you use to accomplish this?

I would do this with two rsync runs from one machine

cd $directory
rsync -e ssh -vaurP ./ $remote:$directory
rsync -e ssh -vaurP $remote:$directory/ .

Better yet, set up the directories in the rsyncd.conf files on
each machine:

cd $directory
rsync -vaurP ./ ${remote}::dir_module/
rsync -vaurP ${remote}::dir_module/ .

Bill
--
INTERNET:   bill at Celestial.COM  Bill Campbell; Celestial Software LLC
UUCP:               camco!bill  PO Box 820; 6641 E. Mercer Way
FAX:            (206) 232-9186  Mercer Island, WA 98040-0820; (206) 236-1676
URL: [http://www.celestial.com/](http://www.celestial.com/)


---

### Post by HermanAB on 2010-04-04
You could use rsync twice, unison or dsync.

Unison would likely be less hassle than rsync.


To bidirectionally sync a directory /src/foo on hostA to /dest/foo on hostB, including all the sub-directories, you would run these commands on hostA:

rsync -auz /src/foo hostB:/dest
rsync -auz hostB:/dest/foo /src

The first command pushes all the files that are newer on hostA to hostB. The second command will pull all the files that are newer on hostB to hostA. The critical options are:
- when copying, you must preserve file modification times. "-a" does this and other things; if you want to preserve just the modification times, use "-t" instead.
- you must skip any files that are newer on the destination: "-u" does this.

Alternatively, you could do the same thing from hostB:

rsync -auz hostA:/src/foo /dest
rsync -auz /dest/foo hostA:/src

---

### Post by The Cog on 2010-04-04
This is the script I use It updates in both directions.```
#!/bin/sh
LOCALDIR=$HOME/Sync/
REMOTEDIR=$HOME/Sync/
if /sbin/route -n | /bin/grep -q '^192.168.1.0 ' 
then 
    SERVER=192.168.1.103
else
    SERVER=xxx.xxx.xxx.xxx
fi
echo Syncing with $SERVER
echo Sending...
rsync --rsh=ssh -aizuKL $LOCALDIR $SERVER:$REMOTEDIR
echo Fetching...
rsync --rsh=ssh -aizuKL $SERVER:$REMOTEDIR $LOCALDIR

```

---

