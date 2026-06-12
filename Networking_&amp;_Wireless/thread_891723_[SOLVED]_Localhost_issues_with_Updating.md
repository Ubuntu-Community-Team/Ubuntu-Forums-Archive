---
title: "[SOLVED] Localhost issues with Updating"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by crazyness003 on 2008-08-16
**[COLOR=Red]EDIT: DO NOT DO WHATEVER IS IN _RED_...IT MIGHT SCREW UP YOUR SYSTEM[/COLOR]**

My last post has some useful info on here, if you wish, read on through or go to my last post on this thread: [http://ubuntuforums.org/showpost.php?p=5609567&postcount=10](http://ubuntuforums.org/showpost.php?p=5609567&postcount=10)

*[COLOR=DarkOliveGreen]START ORIGINAL POST[/COLOR]*
Hey everybody, i hope im in the correct category. I've been having some problems lately since i installed something called "anon-proxy" and another thing called "tor" (I read that they give more anonymity while surfing, and we all know how paranoid one can get about the internet). 
Okay so heres the problem:
    I installed the above 2 packages via "Synaptic" and noticed no difference in anonymity (tested on [http://www.auditmypc.com]("http://www.auditmypc.com/"), it still got my exact location), but i never removed them. After a couple days, i tried firing up Opera Web Browser for some internets but it refused to connect to anything. Bizarrely, Firefox does **not** have this problem. 
To top it all off, when a new update came out today (Aug 16) this is the error message i get when i try to download:
```

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.24/linux-backports-modules-2.6.24-21-generic_2.6.24-21.25_amd64.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

```I looked up the error on the uForums and got to this thread: [http://ubuntuforums.org/showthread.php?t=402504&highlight=connect+localhost%3A4001+(127.0.0.1).+-+(111+Connection+refused)]("http://ubuntuforums.org/showthread.php?t=402504&highlight=connect+localhost%3A4001+%28127.0.0.1%29.+-+%28111+Connection+refused%29") .
So i took the last post's advice, got rid of "anon-proxy" and "tor" and commented 2 entries in my /etc/hosts file. When i do that, a different error shows up but i still cant update and i still cant use Opera. 
```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.24/linux-backports-modules-2.6.24-21-generic_2.6.24-21.25_amd64.deb
  Could not resolve 'localhost'
```I know: WTF?! Right? Anyway, any help would be appreciated.

Heres my /etc/hosts file

```
_**[COLOR=Red]##[/COLOR]**_127.0.0.1 localhost
_**[COLOR=Red]##[/COLOR]**_127.0.0.1 troggie-2    [this is my machine's name]

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```EDIT1: Resolved Opera's lack of connectivity. Somehow the proxy setting in opera was tweaked. It was set to connect through the localhost at port 4001, but when i switched it to "Use proxy for local servers" it works like a charm. 
Is there anywhere i can tweak the Update manager to change proxy settings? Maybe thats where the problem lies.

---

### Post by Naatan on 2008-08-16
Commenting the localhost entry is not a good idea, it will get you into trouble.

Try following the steps in this thread:

[http://forums.debian.net/viewtopic.php?p=1209](http://forums.debian.net/viewtopic.php?p=1209)

---

### Post by crazyness003 on 2008-08-16
[COLOR=RoyalBlue]**DONT MODIFY YOUR ENVIRONMENT**[/COLOR]

okay, i think i remember it asking to do something with /etc/environment so here is that file
```
File: /etc/environment

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

```but now what? on the debian forum all they say is that might have gone wrong, but there is no apparent solution, not to me at least. 
I shoulda never even tried this whole proxy stuff
Unfortunately I uninstalled anon-proxy and when i tried to re-install it, i get the same error message in synaptic.

Okay, as of right now im open to any suggestions. Even if i tank my system, i dont care, its just a reinstall away from working again
:guitar:

---

### Post by crazyness003 on 2008-08-16
I found another post that had some suggestions to fix this (read along to the bottom of the thread)
[http://ubuntuforums.org/showthread.php?t=281428](http://ubuntuforums.org/showthread.php?t=281428)

Unfortunately, none of the suggestions worked for me. And yes it seems like anon-proxy is the culprit for all this mess.

EDIT1:
There is another forum i found that suggested [COLOR=Red]changing the source server from the Software Sources to the "Main Server"[/COLOR]...but it didnt work.
[https://answers.launchpad.net/ubuntu/+question/10408](https://answers.launchpad.net/ubuntu/+question/10408)

---

### Post by Naatan on 2008-08-16
I really think this is a proxy problem, somehow it's resolving whatever url you use to localhost.. 

did you install any proxy-related programs lately? Or any program for that matter that you installed prior to these problems occurring.

---

### Post by crazyness003 on 2008-08-16
Yeah,[COLOR=Red] I installed_ anon-proxy_[/COLOR] and immediately regretted it. I also installed tor. Thats why I uninstalled both completely. but they seem to have left some residue thats messing with my system.
I found at this mailing list [https://lists.ubuntu.com/archives/ubuntu-users/2006-August/090382.html](https://lists.ubuntu.com/archives/ubuntu-users/2006-August/090382.html) 

It has a solution to just edit the Synaptic: Settings -> Preferences -> Network: Proxy Server to "Direct Connect to the Internet", But I already have that configuration, and its not working.

In addition when I issue this command, it gives me the culprit
```
xxx@xxx:~$ echo $http_proxy
http://localhost:4001
```I see that it keeps looking at localhost, but how does one correct this?

---

### Post by Naatan on 2008-08-16
Try the suggestion in the thread I linked above

> As root, just do 'grep -r http_proxy /etc', and as your user yourself, do 'grep -r http_proxy $HOME/.*', that will simply search on both the system-wide config area (/etc) and your user-specific stuff to this setting.

Check the resulting files for a http_proxy setting and clear it.

---

### Post by crazyness003 on 2008-08-16
```
xxx@xxx:~$ sudo grep -r http_proxy /etc/*
Binary file /etc/alternatives/www-browser matches
/etc/bash.bashrc:##export **http_proxy**=
/etc/bash.bashrc:    esacexport **http_proxy**=http://username:password@proxyserver.net:port/
/etc/bash.bashrc~:export **http_proxy**=
/etc/bash.bashrc~:    esacexport **http_proxy**=http://username:password@proxyserver.net:port/
/etc/bash_completion:            -o --output -p --print -P --pgp --proxy --**http_proxy**\
/etc/bash_completion:            -B --bts -l --ldap --no-ldap --proxy= --**http_proxy**= \
/etc/cron.daily/apt:if [ -n "$admin_user" ] && [ -x /usr/bin/sudo ] && [ -z "$**http_proxy**" ] && [ -x /usr/bin/gconftool ]; then
/etc/cron.daily/apt:    use=$(sudo -u "$admin_user" gconftool --get /system/**http_proxy**/use_**http_proxy**)
/etc/cron.daily/apt:    host=$(sudo -u "$admin_user" gconftool --get /system/**http_proxy**/host)
/etc/cron.daily/apt:    port=$(sudo -u "$admin_user" gconftool --get /system/**http_proxy**/port)
/etc/cron.daily/apt:        export **http_proxy**="http://$host:$port/"
/etc/cron.weekly/popularity-contest:  export http_proxy="$**HTTP_PROXY**";
/etc/hwtest.d/hwtest.ini:**http_proxy** = 
/etc/lftp.conf:## Environment variables ftp_proxy,** http_proxy** and no_proxy are used to
/etc/lftp.conf:# set http:proxy your_**http_proxy**[:port]
/etc/lftp.conf:# set hftp:proxy your_**http_proxy**[:port]
/etc/wgetrc:#**http_proxy** = http://proxy.yoyodyne.com:18023/
/etc/wgetrc~:#**http_proxy** = http://proxy.yoyodyne.com:18023/
```This command gives waay too much. I did copy all of it and search through, but all it gave me where entries i typed in the terminal to search for it example
```
grep -r http_proxy $HOME/.*
...
/home/xxx/./.bash_history:echo $http_proxy
/home/xxx/./.bash_history:unset http_proxy
/home/xxx/./.bash_history:echo $http_proxy
/home/xxx/./.bash_history:grep -r http_proxy /etc
...

```Nothing really useful.

I did read this behavior is filed as a bug. [https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/78098](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/78098)
I wonder whats going on.

EDIT1:
I just discovered (thanks to this post [http://ubuntuforums.org/showthread.php?t=480489](http://ubuntuforums.org/showthread.php?t=480489)) how to temporarly allow your source list to communicate to the outside world. I even managed to install some new modules for the new kernel. Of course only using apt-get. The Update Manager still gives me the localhost error
```
xxx@xxx:~$ http_proxy=" "
xxx@xxx:~$ export http_proxy
xxx@xxx:~$ echo $http_proxy
```

---

### Post by Naatan on 2008-08-16
First off your bash.bashrc doesn't have a proxy configured by default.. here's my bash.bashrc (the default). Try using it instead.

**/etc/bash.bashrc**
```
# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm*|rxvt*)
#    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
#    ;;
#*)
#    ;;
#esac

# enable bash completion in interactive shells
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

# sudo hint
if [ ! -e $HOME/.sudo_as_admin_successful ]; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
    cat <<-EOF
    To run a command as administrator (user "root"), use "sudo <command>".
    See "man sudo_root" for details.
    
    EOF
    fi
    esac
fi

# if the command-not-found package is installed, use it
if [ -x /usr/lib/command-not-found ]; then
    function command_not_found_handle {
            # check because c-n-f could've been removed in the meantime
                if [ -x /usr/lib/command-not-found ]; then
           /usr/bin/python /usr/lib/command-not-found -- $1
                   return $?
        else
           return 127
        fi
    }
fi
```

second, it appears /etc/cron.daily/apt uses proxy settings stored in gconf.. try opening the gconf-editor by running: gconf-editor

then click Edit > Find and enter "http_proxy"

 At least one of the results should give "system/http_proxy"

make sure ignore_hosts is set to: [localhost,127.0.0.1,*.local]

The "host" field value should be empty.

Also check the other results to see if you can find possible complications that may cause your problem.

---

### Post by crazyness003 on 2008-08-17
**[COLOR=Red]DO NOT MODIFY YOUR .bash_profile OR .bashrc IT MAY CAUSE PHUNKYNESS WITHIN THE SYSTEM[/COLOR]**
[COLOR=Red]
MODIFY ONLY IF YOU MUST[/COLOR]

> **Naatan said:**
> try opening the gconf-editor by running: gconf-editor

then click Edit > Find and enter "http_proxy"

 At least one of the results should give "system/http_proxy"

make sure ignore_hosts is set to: [localhost,127.0.0.1,*.local]

The "host" field value should be empty.

Also check the other results to see if you can find possible complications that may cause your problem.

I did all what you said, the only thing that was different was instead of ignoring 127.0.0.1, it was ignoring 127.0.0.0/8. Of course i corrected it. There was another entry in "schemas" main (schemas > system > http_proxy), but it was set to <schemas> and was uneditable.

I did however solve the problem somehow. The only thing that i did (beside everything else stated on the threa) was a restart. This unfortunately screwed something else up, or i might have edited something i shouldnt have. Now the gnome-settings-daemon has problems, it takes and additional 5 minutes to load up gnome, and a whole bunch of other garbage. im just gonna reinstall anyway.

So there you have it. Probblem solved with a restart after doing everything else.

what really helped was this[FONT=monospace]
[/FONT]```
http_proxy=" "
export http_proxy
// and then make sure it sticks
echo http_proxy

```or 
> marcobra proposed the following answer:
To find row that set your proxy environment variable:

Open a terminal and type:

grep -i http_proxy .bash_profile

and

grep -i http_proxy .bashrcsee [https://answers.launchpad.net/ubuntu/+question/16262](https://answers.launchpad.net/ubuntu/+question/16262)[B][COLOR=Red]

[/COLOR][/B][COLOR=Red][COLOR=Black]Thanks to [/COLOR][/COLOR][Naatan]("http://ubuntuforums.org/member.php?u=204691") for giving me input and just replying. Your default .bashrc file came in handy (i tanked mine)

---

