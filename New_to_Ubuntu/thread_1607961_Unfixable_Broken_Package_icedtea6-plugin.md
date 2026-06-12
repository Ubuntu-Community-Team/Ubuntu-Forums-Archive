---
title: "Unfixable Broken Package: icedtea6-plugin"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by wigout on 2010-10-28
Hello all,

I have a broken package. I can't fix it.

I've tried synaptic, apt-get, aptitude with various options.

I'm running ubuntu 10.10 by the way.

When I select fix broken package and apply, here's the final error synaptic spits out:
```
E: /var/cache/apt/archives/icedtea6-plugin_6b20-1.9-0ubuntu1_i386.deb: subprocess new pre-removal script returned error exit status 2
```I'd appreciate some tips about what to look at next.

-wigout

Future googlers & whatnot can find the answer to my issue in post #20 of this thread:
[http://ubuntuforums.org/showpost.php?p=10043574&postcount=20](http://ubuntuforums.org/showpost.php?p=10043574&postcount=20)

Another solution from [wyt168]("http://ubuntuforums.org/member.php?u=840993"):
[http://ubuntuforums.org/showpost.php?p=10196369&postcount=25](http://ubuntuforums.org/showpost.php?p=10196369&postcount=25)

and another from [franchoy]("http://ubuntuforums.org/member.php?u=1219698"):
[http://ubuntuforums.org/showpost.php?p=10536652&postcount=28](http://ubuntuforums.org/showpost.php?p=10536652&postcount=28)

---

### Post by alexandari on 2010-10-28
Have you tried launching ubuntu with the recovery mode (from grub) and selecting "fix broken packages" ? It may work...give it a try

---

### Post by arochester on 2010-10-28
Open a Terminal. Try the following commands in turn. 

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update

---

### Post by wigout on 2010-10-28
> **alexandari said:**
> Have you tried launching ubuntu with the recovery mode (from grub) and selecting "fix broken packages" ? It may work...give it a try

I did try, same result.

@arochester:

I cycled through the commands twice. 

Here's a pastebin of what happened:
[http://pastebin.com/DJctBsmT](http://pastebin.com/DJctBsmT) 

in particular the first command and all that unconfigured stuff seems really not right....

Any idea what I should try next?

-wgout

---

### Post by beew on 2010-10-28
I don't know if it is the same problem but I once kind of got stuck in a limbo like that. Here is how I fixed it, may or may not help. But since you have tried all the standard sudo apt-get stuffs randomly you may as well take a look. :)


[URL="http://ubuntuforums.org/showthread.php?t=1597294"] http://ubuntuforums.org/showthread.php?t=1597294
[/URL]

---

### Post by cariboo on 2010-10-28
Use synaptic to remove the broken packages, then clear the archived packages from /var/cache/apt/archives by using the following command:

```
sudo apt-get clean
```

Once all the packages are cleared, try doing the update again.

---

### Post by wigout on 2010-10-28
> **cariboo907 said:**
> Use synaptic to remove the broken packages, then clear the archived packages from /var/cache/apt/archives by using the following command:


Synpatic fails to remove the package (choosing remove and complete removal) and gives this error:
```
E: icedtea6-plugin: subprocess installed pre-removal script returned error exit status 2
```I tried forcing it to upgrade to the lucid version and it said no dice, something like,
No, can't do it, you are holding on to broken pacakges....

Edit: here's the exact error:
```
E: Unable to correct problems, you have held broken packages.
E: Unable to lock the download directory
```



arrgh,

-wigout

---

### Post by beew on 2010-10-28
> **wigout said:**
> Synpatic fails to remove the package (choosing remove and complete removal) and gives this error:
```
E: icedtea6-plugin: subprocess installed pre-removal script returned error exit status 2
```I tried forcing it to upgrade to the lucid version and it said no dice, something like,
No, can't do it, you are holding on to broken pacakges....

Edit: here's the exact error:
```
E: Unable to correct problems, you have held broken packages.
E: Unable to lock the download directory
```

arrgh,

-wigout

Do you have a Lucid version to downgrade to? Did you enable the lucid repositories?

---

### Post by wigout on 2010-10-28
> **beew said:**
> Do you have a Lucid version to downgrade to? Did you enable the lucid repositories?

yep did
sudo vi /etc/apt/sources.list
 and added:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main

and was able in synaptic to choose to force the lucid version-
but when it came to time to apply the changes, I got that error.

-wigout

---

### Post by beew on 2010-10-28
I am wondering what is the meaning of "you have held broken packages". I am sorry if it sounds stupid, but did you have it pinned or something?

---

### Post by beew on 2010-10-28
Ok,

I saw this on the link you posted 
> icedtea6-plugin : Depends: openjdk-6-jre (= 6b18-1.8.1-0ubuntu1) but 6b20-1.9.1-1ubuntu3 is installed

So you have to downgrade openjdk-6-jre first (but you probably can't do it without removing the broken packages first)

By the look of your output it seems that you have not just one, but a whole bunch of broken packages, am I missing something? How did that happen?

---

### Post by wigout on 2010-10-28
Well.... 

I had 10.04 and had the same problem. Couldn't remove/upgrade icedtea6-plugin.

I read about somebody having a similar problem which was solved once they upgraded to 10.10.... but they could only upgrade to 10.10 if they edited out all the half-configured files from:
/var/lib/dpkg/status

Which I did and was permitted to update to 10.10.... with a number of errors.

Apparently I bet on the wrong internet-advice horse this time.

So.... what might do now? Boot up in windows? (after all, I am apparently digging myself an awfully big hole with my sudo powers....)

Any advice is welcome,

-wigout

---

### Post by NightwishFan on 2010-10-28
Try:
```
sudo dpkg -r --force-all *nameofpackage*
```

---

### Post by 73ckn797 on 2010-10-28
> **cariboo907 said:**
> Use synaptic to remove the broken packages, then clear the archived packages from /var/cache/apt/archives by using the following command:

```
sudo apt-get clean
```Once all the packages are cleared, try doing the update again.

This worked when I had similar issue with another package.

---

### Post by theozzlives on 2010-10-28
> **NightwishFan said:**
> Try:
```
sudo dpkg -r --force-all *nameofpackage*
```

I was just about to mention that. That should do a force remove and allow you to do:
```
sudo dpkg -a --configure
```

---

### Post by wigout on 2010-10-28
> **NightwishFan said:**
> Try:
```
sudo dpkg -r --force-all *nameofpackage*
```

```
sudo dpkg -r --force-all icedtea6-plugin
[sudo] password for wigout: 
(Reading database ... 274349 files and directories currently installed.)
Removing icedtea6-plugin ...
update-alternatives: unknown argument `--quiet'

Usage: update-alternatives --install <link> <name> <path> <priority>
       update-alternatives --remove <name> <path>
       update-alternatives --help
<link> is the link pointing to the provided path (ie. /usr/bin/foo).
<name> is the name in /usr/lib/ipkg/alternatives/alternatives (ie. foo)
<path> is the name referred to (ie. /usr/bin/foo-extra-spiffy)
<priority> is an integer; options with higher numbers are chosen.

dpkg: error processing icedtea6-plugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
Errors were encountered while processing:
 icedtea6-plugin

```

---

### Post by wigout on 2010-10-28
So should I be getting myself a livecd and starting over at this point?

Any other options?

---

### Post by wigout on 2010-10-29
So now I have found a number of posts where folks valiantly try to  resolve broken packages by means of commands such as arochester's:
sudo dpkg --configure -a
 sudo apt-get -f install
 sudo apt-get --fix-missing install
 sudo apt-get update
 sudo apt-get dist-upgrade
 sudo apt-get clean
 sudo apt-get autoremove
 sudo apt-get update

and after those fail to work, they resort to reinstalling ubuntu.

Are there any more suggestions on what I can try?

I appreciate any insights, no matter how tenuous,

wigout

---

### Post by sourchier on 2010-10-29
Download the package into your /home directory.

64 bit:

[http://packages.ubuntu.com/lucid-updates/amd64/icedtea6-plugin/download]("http://packages.ubuntu.com/lucid-updates/amd64/icedtea6-plugin/download")

32 bit:
[http://packages.ubuntu.com/lucid-updates/i386/icedtea6-plugin/download]("http://packages.ubuntu.com/lucid-updates/i386/icedtea6-plugin/download")

Install the package using the command sudo dpkg -i icedtea6-plugin-*. If you get any errors just post them here.

---

### Post by wigout on 2010-10-29
So here's the prerm "preremoval" script inside:
icedtea6-plugin_6b20-1.9.1-1ubuntu3_i386.deb

that's giving the error 
installed pre-removal script returned error exit status 2

```
#!/bin/sh -e

browser_dirs="mozilla"
PLUGIN=IcedTeaPlugin.so
PLUGINPTH=/usr/lib/jvm/java-6-openjdk/jre/lib/i386/$PLUGIN

for browser_dir in $browser_dirs; do
    if [ $browser_dir = xulrunner-addons ]; then
        browser=xulrunner-1.9
    else
        browser=$browser_dir
    fi
    update-alternatives --quiet --remove \
    $browser-javaplugin.so \
    $PLUGINPTH
done
```

/usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so exists
$browser-javaplugin.so
or
mozilla-javaplugin.so, in my case, doesn't exist anywhere that I search for it.

The home/user/.mozilla/plugins/ directory is empty.

When I ran 
update-alternatives --quiet --remove mozilla-javaplugin.so /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so

on the commandline, I get:
update-alternatives: unknown argument `--quiet'

So I googled "update-alternatives --quiet"

found this:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg447812.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg447812.html)

It was a PATH error!

which -a update-alternatives
/usr/local/bin/update-alternatives
 /usr/sbin/update-alternatives
/usr/bin/update-alternatives

To temporarily fix this issue, I:
sudo mv /usr/local/bin /usr/local/bun

Ran synaptic. It fixed the package.

Now how do I fix it for good?
Do I edit my .profile or something else?

-wigout

---

### Post by migs73 on 2010-10-29
Try post #11 on this thread;

[http://ubuntuforums.org/showthread.php?t=1597784](http://ubuntuforums.org/showthread.php?t=1597784)

---

### Post by wigout on 2010-10-29
So, just one last thing before I mark this solved:
How do I fix my path problem noted in post number 20?

Thanks,
wigout

---

### Post by sourchier on 2010-10-29
You can change your path settings using the information provided here:

[http://ubuntuforums.org/showthread.php?t=1457207&highlight=updating+%24path]("http://ubuntuforums.org/showthread.php?t=1457207&highlight=updating+%24path")

and here:

[http://ubuntuforums.org/showthread.php?t=1604568&highlight=updating+%24path]("http://ubuntuforums.org/showthread.php?t=1604568&highlight=updating+%24path")

My /etc/environment has PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
 in it.

And when I echo $PATH I get this output:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

What does your settings look like?

---

### Post by wigout on 2010-10-29
my PATH looks about the same as yours, with more ad-hoc add-in paths at the end.

My conflict was with the ipkg-cl & update-alternatives there in the /usr/local/bin

I have fooled around with ipkg in the past, but I can't for the life of me remember installing it and it doesn't show any packages installed. Maybe it was "part" of some other manual install and I have forgotten.

On the off chance that it might yet be needed, I renamed /usr/local/bin/update-alternatives to /usr/local/bin/maybe-delete-update-alternatives.
(I also renamed /usr/local/bin/ipkg-cl to /usr/local/bin/maybe-delete-ipkg-cl)

Anyway solved and solved.

Thanks for everyone's ideas and advice.

-wigout

---

### Post by wyt168 on 2010-12-03
> **wigout said:**
> 

When I ran 
update-alternatives --quiet --remove mozilla-javaplugin.so /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so

on the commandline, I get:
update-alternatives: unknown argument `--quiet'

So I googled "update-alternatives --quiet"

found this:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg447812.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg447812.html)

It was a PATH error!

which -a update-alternatives
/usr/local/bin/update-alternatives
 /usr/sbin/update-alternatives
/usr/bin/update-alternatives

-wigout

I have exactly the same problem, except that I don't have a bogus update-alternatives in my /usr/local/bin.

```
wtsai@ubuntu-9:~$ which -a update-alternatives
/usr/sbin/update-alternatives
/usr/bin/update-alternatives
```However, when I ran update-alternatives, I got a different error:
```
wtsai@ubuntu-9:~$ update-alternatives --quiet --remove mozilla-javaplugin.so /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so
update-alternatives: error: while reading /var/lib/dpkg/alternatives/mozilla-javaplugin.so: Bad file descriptor
```Turned out that there are 2 mozilla-javaplugin.so on my system,
```
wtsai@ubuntu-9:~$ find / -maxdepth 5 -name "mozilla-javaplugin.so" 2>/dev/null 
/var/lib/dpkg/alternatives/mozilla-javaplugin.so
/etc/alternatives/mozilla-javaplugin.so

``` and update-alternatives is having trouble with the one under  /var/lib/dpkg/alternatives and the one under /etc/alternatives is  actually pointing to the file  /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so:
```
wtsai@ubuntu-9:~$ ls -l /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 root root 57 2010-06-01 15:58 /etc/alternatives/mozilla-javaplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so
wtsai@ubuntu-9:~$ ls -l /var/lib/dpkg/alternatives/mozilla-javaplugin.so
-rw-r--r-- 1 root root 112 2010-06-01 15:58 /var/lib/dpkg/alternatives/mozilla-javaplugin.so
```After renaming /var/lib/dpkg/alternatives/mozilla-javaplugin.so to something else, I was able to run Synaptic and finish the update.

I am not sure why I got a bad file descriptor error while trying to remove /var/lib/dpkg/alternatives/mozilla-javaplugin.so. Any suggestion? 

p.s. @wigout: could you provide a link to this post as an alternative solution at the beginning of this thread in post#1 as what you did with your post#20? I am afraid my post here might get buried in the thread and other people may not be able to find it.
Thx!

---

### Post by JTempelm on 2011-01-09
Thank you! What wyt168 suggests in post #25 worked for me I've been trying to fix this for awhile.

---

### Post by franchoy on 2011-03-08
> **wigout said:**
> So here's the prerm "preremoval" script inside:
icedtea6-plugin_6b20-1.9.1-1ubuntu3_i386.deb

that's giving the error 
installed pre-removal script returned error exit status 2

```
#!/bin/sh -e

browser_dirs="mozilla"
PLUGIN=IcedTeaPlugin.so
PLUGINPTH=/usr/lib/jvm/java-6-openjdk/jre/lib/i386/$PLUGIN

for browser_dir in $browser_dirs; do
    if [ $browser_dir = xulrunner-addons ]; then
        browser=xulrunner-1.9
    else
        browser=$browser_dir
    fi
    update-alternatives --quiet --remove \
    $browser-javaplugin.so \
    $PLUGINPTH
done
```

/usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so exists
$browser-javaplugin.so
or
mozilla-javaplugin.so, in my case, doesn't exist anywhere that I search for it.

The home/user/.mozilla/plugins/ directory is empty.

When I ran 
update-alternatives --quiet --remove mozilla-javaplugin.so /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so

on the commandline, I get:
update-alternatives: unknown argument `--quiet'

So I googled "update-alternatives --quiet"

found this:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg447812.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg447812.html)

It was a PATH error!

which -a update-alternatives
/usr/local/bin/update-alternatives
 /usr/sbin/update-alternatives
/usr/bin/update-alternatives

To temporarily fix this issue, I:
sudo mv /usr/local/bin /usr/local/bun

Ran synaptic. It fixed the package.

Now how do I fix it for good?
Do I edit my .profile or something else?

-wigout

how did you specifically fixed it? can you post a step by step, cause I'm kinda stuck with it.... Because of it I can't install anything....

---

### Post by franchoy on 2011-03-08
found a permanent fix on our problem. This is not really a problem with icedtea6-plugin. its a weird problem with plymouth theme. here's the code you need:

```


sudo mv /lib/plymouth/themes/tema /tmp/tema

sudo mkdir /lib/plymouth/themes/tema

sudo mv /tmp/tema /lib/plymouth/themes/tema/sfondo.plymouth

sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth 100

 sudo apt-get upgrade


```

Solution provided by Bman from friendlycoders...

---

