---
title: "package manager no longer working correctly"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by AmberG on 2009-03-29
Everything was working fine until a couple of days ago.
Now. usual red arrow telling me 25 updates ready.
I click on arrow which opens package manager as usual.
But when I click "Install" I get "An error occurred dialog" with the following message repeated:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

Obviously a daft message as I am connected to post this and can access internet/email/ftp with no problems. The bit "localhost:4001" doesn't seem to make sense to me either.

Nothing (other than updates) downloaded since it last worked. Nothing changed on system AFAIK.
v.8.10

Any help appreciated - note I'm still a novice who expects things to work out of the box and keep working ;)

---

### Post by thunk77 on 2009-03-29
Hello,

Can you open a terminal and enter
```
sudo apt-get update && sudo apt-get upgrade
```
and post the output it gives you here?

Btw, terminal is located at Applications->Places->System

---

### Post by AmberG on 2009-03-29
Hello thunk77,
Similar message:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/restricted Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

repeated 25 times followed by:

Reading package lists... Done

followed by:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

repeated 25 times !

followed by:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by namaku0 on 2009-03-29
Can you post your:
/etc/apt/sources.list
/etc/hosts
/etc/resolv.conf

---

### Post by thunk77 on 2009-03-29
Hmmmm,

How about going to System->Preferences->Network Proxy
Is it set to Direct Internet Connection?

Also, In the "Preferences" dialog in Synaptic Package Manager, is it set to Direct Internet Connection also in the "Network" tab?

---

### Post by AmberG on 2009-03-29
> **namaku0 said:**
> Can you post your:
/etc/apt/sources.list
/etc/hosts
/etc/resolv.conf

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main universe restricted multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main universe restricted multiverse

deb http://archive.ubuntu.com/ubuntu/ intrepid-proposed universe main multiverse restricted
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```


Sorry can't post the hosts file as it has confidential company info in it but it has not changed since system set up and has been working fine for all connections (and still is for all others) up to recently.

The resolve.conf file has only 3 lines also confidential:
domain *** our local domain here ***
search *** our local domain here ***
nameserver *** our internal network IP eg 192.*.*.*

---

### Post by AmberG on 2009-03-29
> **thunk77 said:**
> Hmmmm,

How about going to System->Preferences->Network Proxy
Is it set to Direct Internet Connection?

Also, In the "Preferences" dialog in Synaptic Package Manager, is it set to Direct Internet Connection also in the "Network" tab?

Yes
and
Yes

---

### Post by thunk77 on 2009-03-29
Well, something obviously has changed otherwise you wouldn't have this problem. I browsed some of your older posts and it seems that you have been using aptitude for updates, right? Have you also been using apt-get mixed with aptitude? If you have, it's a sure way to mess up something in your system. Aptitude treats packages differently in respect with dependencies and autoremove functions. I'm not an expert on aptitude but maybe someone else can help. Good luck.

---

### Post by hyper_ch on 2009-03-29
try to set the according country mirrors for the official ubuntu repos. You can use the generator in my sig.

---

### Post by namaku0 on 2009-03-29
How about posting only /etc/hosts entry that started with
127.0.*.* ? Thats should be okay.

---

### Post by AmberG on 2009-03-29
> **thunk77 said:**
> Well, something obviously has changed otherwise you wouldn't have this problem. I browsed some of your older posts and it seems that you have been using aptitude for updates, right? Have you also been using apt-get mixed with aptitude? If you have, it's a sure way to mess up something in your system. Aptitude treats packages differently in respect with dependencies and autoremove functions. I'm not an expert on aptitude but maybe someone else can help. Good luck.

You have confused me - I said I was a beginner.

I don't know what I use other than what was working - is for some reason - no longer working.

All I know is that every day the system automatically checks for updates (I don't know if that is apt-get or aptitude :( ) and every couple of days or so the red arrow appears saying that there is x updates. I then click on it as indicated and the package manager starts up giving the option to install which I do without understanding all the updates.

In the past it worked - now it just shouts at me with this cannot connect nonsense.

Thanks for trying anyway.

---

### Post by AmberG on 2009-03-29
> **hyper_ch said:**
> try to set the according country mirrors for the official ubuntu repos. You can use the generator in my sig.

Sorry, but that doesn't make much sense to me I don't understand what boxes to tick and what not to.

AND I'm VERY worried that by changing the current list I will miss out on some of the key updates required by the software / system.

It is not that I don't trust - it is just that I do not understand.

and especially why something works on day and not the next when nothing has been knowingly changed.

---

### Post by AmberG on 2009-03-29
> **namaku0 said:**
> How about posting only /etc/hosts entry that started with
127.0.*.* ? Thats should be okay.

as you can see there is still nothing that can be published - the machine is used for website development so under "censored" are the "local" site domains.  This has not changed for months and works perfectly.  I don't know where the Ip6 stuff originates from or what it does - again it has been there for ages so didn't affect updates in the past so why should it suddenly do so now?



```

127.0.0.1	localhost
127.0.0.1	censored.localhost
127.0.0.1	censored_co_uk
127.0.0.1	censored.localhost
127.0.0.1	censored_co_uk
127.0.0.1	censored.localhost
127.0.0.1	censored_co_uk
127.0.0.1	censored.localhost
127.0.0.1	censored_co_uk

127.0.1.1	local

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


```

---

### Post by hovzio on 2009-03-29
> **thunk77 said:**
> Well, something obviously has changed otherwise you wouldn't have this problem. I browsed some of your older posts and it seems that you have been using aptitude for updates, right? Have you also been using apt-get mixed with aptitude? If you have, it's a sure way to mess up something in your system. Aptitude treats packages differently in respect with dependencies and autoremove functions. I'm not an expert on aptitude but maybe someone else can help. Good luck.

Is this really true that one shouldn't use apt-get and aptitude in unison?Never heard of this but if its true its good to know about. I know one of the differences is that aptitude also installs all suggested packages while apt-get does not. Guess I'm gonna read into this a little, thanks for the info.

Edit: Where does dpkg come in?

---

### Post by thunk77 on 2009-03-29
dpkg is the base for the Debian package system. Basically it's a low-level tool that doesn't deal with dependencies of any kind and it is the basis upon apt or aptitude functions are built.

---

### Post by AmberG on 2009-03-30
> **thunk77 said:**
> dpkg is the base for the Debian package system. Basically it's a low-level tool that doesn't deal with dependencies of any kind and it is the basis upon apt or aptitude functions are built.

thunk77, I know that response is not in answer to my question but hovzio's post.

But for the ignorant "beginner" here you/someone could elaborate - NOW there seems "suddenly to me" to be 3 different update "packages" 
dpkg ? "the basis of the other two"
apt ? - I thought was just an abbreviation for
aptitude ?

now all I was aware of was System/Administration/Synaptic Package Manager and System/Administration/Update Manager -- which actually I thought was the same "update manager" but in two different approaches ... the first allows the addition of new packages not yet installed where as the second enables the "automatic" update of those packages (and the one that produces that daily red arrow on the status panel) I do not know of either of them as apt or aptitude.

as for dpkg if that is a basis for the other two? isn't that just confusing the issue further. ... and if you shouldn't use both of them together then how can you load a new package with System/Administration/Update Manager ? ... and shouldn't they each come with a warning about the other one?

This just seems madder and madder and get's nowhere in making life simpler.

BTW. I'm now up to 29 updates that fail to download

---

### Post by namaku0 on 2009-03-30
> **AmberG said:**
> as you can see there is still nothing that can be published - the machine is used for website development so under "censored" are the "local" site domains.  This has not changed for months and works perfectly.  I don't know where the Ip6 stuff originates from or what it does - again it has been there for ages so didn't affect updates in the past so why should it suddenly do so now?



```

127.0.0.1	localhost
127.0.0.1	censored.localhost
127.0.0.1	censored_co_uk
127.0.0.1	censored.localhost
127.0.0.1	censored_co_uk
127.0.0.1	censored.localhost
127.0.0.1	censored_co_uk
127.0.0.1	censored.localhost
127.0.0.1	censored_co_uk

127.0.1.1	local

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


```

> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...id/Release.gpg](http://archive.ubuntu.com/ubuntu/dis...id/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

The updater trying to fetch file from archive.ubuntu.com 
which should be on 91.189.88.31, but instead it connect to
your own computer (127.0.0.1) on port 4001. Thats why I
thought you have domain name resolving problem.

Open Terminal (Applications > Accessories > Terminal)
Type **echo $http_proxy** and press enter. What is
the output?

Did you by chance installed the **anon-proxy** package?
If yes, disable or even uninstall it.

---

### Post by AmberG on 2009-03-30
> **namaku0 said:**
> The updater trying to fetch file from archive.ubuntu.com 
which should be on 91.189.88.31, but instead it connect to
your own computer (127.0.0.1) on port 4001. Thats why I
thought you have domain name resolving problem.

Open Terminal (Applications > Accessories > Terminal)
Type **echo $http_proxy** and press enter. What is
the output?

Did you by chance installed the **anon-proxy** package?
If yes, disable or even uninstall it.

Thanks namaku0

```

http://localhost:4001

```

No I don't have **anon-proxy** installed - I've just checked in System/Administraion/Synaptic Package Manager and when I search for "anon-proxy" the box is clear/unchecked.

But Tor was installed when the system was set up months ago - but it has never worked properly (that's a separate issue of little concern atm).  

As I've said - everything used to work AND I can still connect to all other sites including ftp connections so surely if a proxy was getting in the way it would affect every connection not just 91.189.88.31

---

### Post by namaku0 on 2009-03-30
Again, open the Terminal. Write:
**unset http_proxy**

After that try to update again.

---

### Post by AmberG on 2009-03-30
> **namaku0 said:**
> Again, open the Terminal. Write:
**unset http_proxy**

After that try to update again.

the output from echo $http_proxy is now empty

but. still the same set of error messages from System/Administration/Update Manager :(

nice try, namaku0, you had me hopeful for a minute there ;)

---

### Post by namaku0 on 2009-03-30
How about updating from Terminal?
[B]sudo apt-get update
sudo apt-get dist-upgrade[/B]

Can you open this link with Firefox?
[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

---

### Post by AmberG on 2009-03-30
> **namaku0 said:**
> How about updating from Terminal?
[B]sudo apt-get update
sudo apt-get dist-upgrade[/B]

Can you open this link with Firefox?
[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

those commands in terminal still give the same error messages as above.

The url in Firefox 
gives a directory listing:
```

Index of /ubuntu
[ICO]	Name	Last modified	Size
[DIR]	Parent Directory	 	- 	 
[DIR]	dists/	04-Dec-2008 22:08 	- 	 
[DIR]	indices/	30-Mar-2009 13:43 	- 	 
[ ]	ls-lR.gz	30-Mar-2009 13:42 	6.4M	 
[DIR]	pool/	14-Jan-2008 22:05 	- 	 
[DIR]	project/	13-Feb-2008 14:39 	- 	 
Apache/2.2.8 (Ubuntu) Server at archive.ubuntu.com Port 80

```

---

### Post by kevmitch on 2009-03-30
When you unset http_proxy, that only applies to the terminal window you have opened. Unsetting http_proxy in the terminal will not effect System/Administration/Update Manager. 

Did you try using 

```

unset http_proxy 
sudo apt-get update && sudo apt-get upgrade

```
all in the same terminal. 

We should also figure out why http_proxy is getting set. There are two places I can think to look:

in your home directory
```

grep http_proxy ~/.* 

```

and in the /etc/ directory
```

sudo grep -R http_proxy /etc/ 2> /dev/null

```

that second one might take a while to run.

---

### Post by namaku0 on 2009-03-30
Look at this thread too: 
[http://ubuntuforums.org/showthread.php?t=936625](http://ubuntuforums.org/showthread.php?t=936625)

Summary: 
Uninstall **tor**. You may need to restart the computer.

---

### Post by AmberG on 2009-03-30
> **kevmitch said:**
> When you unset http_proxy, that only applies to the terminal window you have opened. Unsetting http_proxy in the terminal will not effect System/Administration/Update Manager. 

Did you try using 

```

unset http_proxy 
sudo apt-get update && sudo apt-get upgrade

```
all in the same terminal. 


Sorry, I didn't realise that the unset had to be repeated.
But  GREAT NEWS!!!
That worked and updates seemed to go through with only one warning.
```

W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

```

Many Thanks


> **kevmitch said:**
> 
We should also figure out why http_proxy is getting set. There are two places I can think to look:

in your home directory
```

grep http_proxy ~/.* 

```


```

:~$ grep http_proxy ~/.* 
/home/amber/.bash_history:echo $http_proxy
/home/amber/.bash_history:unset http_proxy
/home/amber/.bash_history:echo http_proxy
/home/amber/.bash_history:echo $http_proxy
grep: /home/amber/.nano_history: Permission denied

```

> **kevmitch said:**
> 
and in the /etc/ directory
```

sudo grep -R http_proxy /etc/ 2> /dev/null

```

that second one might take a while to run.

It did but responded with gibberish to me - hope it makes sense to you.
```

:/etc$ sudo grep -R http_proxy /etc/ 2> /dev/null
/etc/pear/pear.conf:a:29:{s:9:"cache_dir";s:15:"/tmp/pear/cache";s:15:"default_channel";s:12:"pear.php.net";s:16:"preferred_mirror";s:12:"pear.php.net";s:13:"remote_config";s:0:"";s:13:"auto_discover";i:0;s:13:"master_server";s:12:"pear.php.net";s:10:"http_proxy";s:0:"";s:7:"php_dir";s:14:"/usr/share/php";s:7:"ext_dir";s:26:"/usr/lib/php5/20060613+lfs";s:7:"doc_dir";s:18:"/usr/share/php/doc";s:7:"bin_dir";s:8:"/usr/bin";s:8:"data_dir";s:19:"/usr/share/php/data";s:7:"cfg_dir";s:18:"/usr/share/php/cfg";s:7:"www_dir";s:18:"/usr/share/php/www";s:8:"test_dir";s:19:"/usr/share/php/test";s:8:"temp_dir";s:14:"/tmp/pear/temp";s:12:"download_dir";s:44:"/build/buildd/php5-5.2.6/pear-build-download";s:7:"php_bin";s:12:"/usr/bin/php";s:7:"php_ini";s:0:"";s:8:"username";s:0:"";s:8:"password";s:0:"";s:7:"verbose";i:1;s:15:"preferred_state";s:6:"stable";s:5:"umask";i:18;s:9:"cache_ttl";i:3600;s:8:"sig_type";s:3:"gpg";s:7:"sig_bin";s:12:"/usr/bin/gpg";s:9:"sig_keyid";s:0:"";s:10:"sig_keydir";s:18:"/etc/pear/pearkeys";}
/etc/hwtest.d/hwtest.ini:http_proxy = 
/etc/cron.weekly/popularity-contest:  export http_proxy="$HTTP_PROXY";
/etc/lftp.conf:## Environment variables ftp_proxy, http_proxy and no_proxy are used to
/etc/lftp.conf:# set http:proxy your_http_proxy[:port]
/etc/lftp.conf:# set hftp:proxy your_http_proxy[:port]
Binary file /etc/alternatives/www-browser matches
/etc/bash_completion:			-o --output -p --print -P --pgp --proxy --http_proxy\
/etc/bash_completion:			-B --bts -l --ldap --no-ldap --proxy= --http_proxy= \
Binary file /etc/razorsql/jre/lib/i386/libnet.so matches
Binary file /etc/razorsql/jre/lib/i386/libdeploy.so matches
/etc/wgetrc:#http_proxy = http://proxy.yoyodyne.com:18023/
/etc/cron.daily/apt:if [ -n "$admin_user" ] && [ -x /usr/bin/sudo ] && [ -z "$http_proxy" ] && [ -x /usr/bin/gconftool ]; then
/etc/cron.daily/apt:	use=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/use_http_proxy)
/etc/cron.daily/apt:	host=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/host)
/etc/cron.daily/apt:	port=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/port)
/etc/cron.daily/apt:		export http_proxy="http://$host:$port/"

```

and who the heck are yoyodyne.com or shouldn't I ask ?

---

### Post by AmberG on 2009-03-30
> **namaku0 said:**
> Look at this thread too: 
[http://ubuntuforums.org/showthread.php?t=936625](http://ubuntuforums.org/showthread.php?t=936625)

Summary: 
Uninstall **tor**. You may need to restart the computer.

Am I mistaken? But that thread is about **anon-proxy** something we have already dismissed because I don't have it.

I do have Tor - have had Tor installed for ages while Package Manager has been working. But Tor itself has never worked (something to fix at a later date probably) - that does not seem like a reason to remove it.

---

### Post by kevmitch on 2009-03-30
Mmm, well I don't see any obvious places where the http_proxy is getting into the environment. I might try uninstalling tor. I don't see uninstalling it hurting if it's not working right now. Additionally, unless you're attached to any configurations you made with it, you might want to purge those too

```

aptitude purge tor

```

Does anybody else have any ideas as to where this variable might get set?

As for [yoyodyne]("http://en.wikipedia.org/wiki/Yoyodyne"), I think that's a geek joke (if you hadn't guessed Linux is full of them)

---

### Post by WhatamImissing? on 2009-03-31
I'm having the same problem as Amber but it might be for a different reason.  I've been through the solutions of this thread and unfortunately they did not work for me.  My "Add/Remove Applications", "Software Sources" and "Synaptic Package Manager" all reach the same ultimate point:

Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

This past weekend I saw a couple of commands on this forum that had to do with erasing old, unused files.  I think they were sudo apt- commands, but I can't figure out what they were now and I am wondering if they had anything to do with my problem.

I had anon-proxy installed but removing it (and rebooting) didn't help.

---

### Post by AmberG on 2009-03-31
> **kevmitch said:**
> Mmm, well I don't see any obvious places where the http_proxy is getting into the environment. I might try uninstalling tor. I don't see uninstalling it hurting if it's not working right now. Additionally, unless you're attached to any configurations you made with it, you might want to purge those too

```

aptitude purge tor

```

Does anybody else have any ideas as to where this variable might get set?

As for [yoyodyne]("http://en.wikipedia.org/wiki/Yoyodyne"), I think that's a geek joke (if you hadn't guessed Linux is full of them)

Well a new day and a new reboot !!
Whatever was downloaded in updates yesterday must have fixed the problem.
Without a tor purge. The daily update started this morning and loaded another 5 updates without having to go back through terminal and unset.. etc.

Special thanks to kevmitch, as it was your suggestion that enable me to get past those error messages. 

I also did another echo $http_proxy and now get a blank line - so something worked.

Geek joke - I don't understand - but perhaps that's the joke - hey ho

Thanks everyone for help.

---

### Post by WhatamImissing? on 2009-03-31
I don't know why but everything that didn't work last night is working this morning.  Got my updates...no help necessary...but this thread was useful.  Thanks all.

---

