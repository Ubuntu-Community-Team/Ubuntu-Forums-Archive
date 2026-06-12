---
title: "wireless and 7.04??"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by gatoruss on 2007-05-20
Hi, I recently upgrade to 7.04.  Prior to upgrade, I had wireless working fine.  I had a linksys, and configured using [http://ubuntuforums.org/showthread.php?t=318539]("http://ubuntuforums.org/showthread.php?t=318539").

Now it does not work.  I tried to reconfigure using same link, but when I run restart I am told that wlan0 cannot be found?

Any suggestions?

---

### Post by DougB1958 on 2007-05-20
Are you using a LinkSys wireless card with an RaLink RT2xxx/RT61 chipset?

(To find out what chipset your card uses, open a terminal window and type the command

```
lspci
```

Look in the output for a line that mentions "network controller" or "802.11" -- on my computer, the line in question reads

```
06:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI
```

and "RaLink RT2561/RT61" is the key phrase.)

If you are using the RT2xxx/RT61, then the note about RT2xxx drivers not supporting the approach in the post you cite (item 6 under "Common Stumbling Blocks") may be the thing that solves your problem -- it did for me. In particular, the site that note links to ([http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=21546&sid=c5e02ed97dde07681fb564639e9f50c5]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=21546&sid=c5e02ed97dde07681fb564639e9f50c5")) has instructions for manually configuring WPA that I was able to adapt to Ubuntu. Specifically, I did the following:

Write a shell script containing the following:

```
#!/bin/sh
iwconfig ra0 essid <Your-Access-Point-SSID>
iwpriv ra0 set AuthMode=WPAPSK
iwpriv ra0 set EncrypType=AES
iwpriv ra0 set WPAPSK=<Your-PSK>
```

Note that "ra0" is the name of the rt2xxx-based wireless interface in 7.04. Some details of this script may differ for you, particularly the encryption type (the other choice is TKIP, if I remember right). You can find out your PSK using wpa-passphrase, as described in [http://ubuntuforums.org/showthread.php?t=318539]("http://ubuntuforums.org/showthread.php?t=318539"). I put this script in a file named "/etc/network/if-pre-up.d/rt61wpa".

Next, I edited "/etc/network/interfaces" to contain the following section (replacing whatever was already there for interface ra0, and leaving the sections for other interfaces alone):

```
auto ra0
iface ra0 inet dhcp
  pre-up /etc/network/if-pre-up.d/rt61wpa
  wireless-essid <Your-Access-Point-SSID>
```

The last line may not be necessary (it's left over from 6.10).

Finally, I got rid of the network-manager (by using Synaptic to remove it), since I understand that it interferes with network configuration via "/etc/network/interfaces".

Hope this helps. (And I hope others feel free to jump in with alternative ideas, corrections, etc. -- this is my first post to the Ubuntu forums, and I can't help feeling that trying to answer someone else's questions instead of asking my own is an over-ambitious way to start :))

---

### Post by gatoruss on 2007-05-22
Thanks for you help....

...I tried to do what you suggest, and when I run "sudo /etc/init.d/networking restart," I get   

>  * Reconfiguring network interfaces...
/bin/sh: /etc/network/if-pre-up.d/rt61wpa: Permission denied
Failed to bring up ra0.

Very frustrating....this shouldn't be this hard....:icon_frown:

---

### Post by DougB1958 on 2007-05-22
This looks mildly encouraging -- at least the system is trying to run your set-up script.

Who owns "rt61wpa," and what are its permissions? If you open a terminal window and issue the command

```
ls -l /etc/network/if-pre-up.d/rt61wpa
```

you should see output like

```
-rwx------ 1 root root 185 2007-05-17 21:41 /etc/network/if-pre-up.d/rt61wpa
```

The crucial things to look for here are the "x" in "rwx" (which means that the script is executable by its owner), and the "root root" part (which means that the root user owns the script). If either of these things is missing, you can fix them with the following commands -- the second makes "root" own the script, and the third adds the "x" (executable) permission:

```
cd /etc/network/if-pre-up.d
sudo chown root:root rt61wpa
sudo chmod u+x rt61wpa
```

My guess is that you are missing the executable permission, for which I apologize -- I should have mentioned the "chmod" command when I suggested putting the set-up commands in a script.

Good luck, and let me know if any of this helps.

---

### Post by gatoruss on 2007-05-23
Ok, I tried ran "ls -l /etc/network/if-pre-up.d/rt61wpa" and the result _[COLOR="Red"]did not [/COLOR]_have the "x", _[COLOR="red"]had[/COLOR]_ "r" for user and group and [COLOR="red"]_did not _[/COLOR]list "root as owner, so I ran

> cd /etc/network/if-pre-up.d
sudo chown root:root rt61wpa
sudo chmod u+x rt61wpa

When I ran "ls -l /etc/network/if-pre-up.d/rt61wpa" again I got

> -rwxr--r-- 1 root root 196 2007-05-23 19:18 /etc/network/if-pre-up.d/rt61wpa

Then when I ran "sudo /etc/init.d/networking restart," I got

>  * Reconfiguring network interfaces...                                          /bin/sh: /etc/network/if-pre-up.d/rt61wpa: not found
Failed to bring up ra0.

If I got to /etc/network/if-pre-up.d/ in the file browser, it shows ft61wpa with a lock icon on it.

---

### Post by DougB1958 on 2007-05-23
Hmm. The commands you issued and the output you got look good (up 'til you tried to restart the network, of course). Fixing the execute permission is definitely progress. I think the lock icon you see on "rt61wpa" in the file browser just means that you don't have write access to that file (which is reasonable, since only its owner -- root -- has write access).

Now I'm starting to suspect a typo in the "rt61wpa" script file perhaps. Can you check that it contains exactly the text I posted earlier in this thread, except with "<Your-Access-Point-SSID>" replaced with whatever the name of your access point is, and "<Your-PSK>" replaced with your PSK? (No angle brackets around the actual SSID and PSK, by the way.) Or post it here, and I'll see if I spot anything suspicious in it.

It might also be informative to see if you can execute the "rt61wpa" script manually, i.e., try issuing the following command from a terminal window:

```
sudo /etc/network/if-pre-up.d/rt61wpa
```

If this runs without errors, then maybe the problem with running it via "/etc/init.d/networking" is a typo in "/etc/network/interfaces" (although that seems unlikely, unless you have recently edited that file, since a couple of days ago "/etc/init.d/networking" seemed able to find the script). If you can run the "rt61wpa" script manually, then afterwards you should be able to finish bringing up your wireless interface with the command
 
```
sudo ifup ra0
```

(Not that these are things you want to do by hand every time you want to bring up your wireless network, of course, but their success or failure may shed more light on why it won't run automatically.)

---

### Post by gatoruss on 2007-05-23
Appreciate you sticking with me....did not work....here is what I got:

> 
~$ sudo /etc/network/if-pre-up.d/rt61wpa
Password:
sudo: unable to execute /etc/network/if-pre-up.d/rt61wpa: No such file or directory


Checked in the file browser....file does exist!

---

### Post by DougB1958 on 2007-05-24
Well, this tells us something, although it's surprising -- something on the path "/etc/network/if-pre-up.d/rt61wpa" doesn't exist, or at least can't be found by the shell. Some possible explanations....

1. Any chance that the "if-pre-up.d" directory has inadvertently been renamed? (I think if "etc" or "network" had been renamed there would be much more obvious problems)

2. Any chance that "if-pre-up.d" or "rt61wpa" have been inadvertently renamed in ways that would be hard to spot from the file browser (e.g., a space or other non-printing character inserted before or after the printable part of the file name)? The terminal command

```
ls -b
```

will print a list of the files in a directory with non-printing characters preceded by a "\" escape character. For example, here's one of my directories in which I've put a space at the end of one of the file's names displayed with and without the "-b" option on "ls":

```
doug@ubuntu:~/DevTest$ ls
Makefile  README.txt  test.c   test.cpp
doug@ubuntu:~/DevTest$ ls -b
Makefile  README.txt  test.c\   test.cpp
```

So try the commands

```
ls -b /etc/network
ls -b /etc/network/if-pre-up.d
```

and look to see if "if-pre-up.d" or "rt61wpa" show up with backslashes in unexpected places.

3. Any chance that the "if-pre-up.d" directory is no longer searchable by the root user (so that the system can't look inside it for "rt61wpa")? To check this, issue the command

```
ls -ld /etc/network/if-pre-up.d
```

and check to see that the directory has "r" and "x" permissions for its owner, group, and world (owner is probably enough, but it might as well have them for everyone). In other words, the "ls" command should produce output similar to this:

```
drwxr-xr-x 2 root root 4096 2007-05-17 21:41 /etc/network/if-pre-up.d
```

---

### Post by gatoruss on 2007-05-24
Doug -

I think that this thread might be the answer to my problem..[rt61 and Ubuntu Feisty Fawn, 7.04, WPA-PSK problems solved]("rt61 and Ubuntu Feisty Fawn, 7.04, WPA-PSK problems solved").  I am stuck on step (d)...any thoughts?

---

### Post by DougB1958 on 2007-05-26
I think the directions you're following refer to editing the "rt61sta.dat" file using "vim", right?


vim is a text editor, dating to the early days of Unix but still popular. The basic editing model is that you have a full-window view of the text in the file you are editing, and by default anything you type is interpreted as a command to the editor (in contrast to, e.g., gedit, where by default anything you type is interpreted as text to insert into the file, and commands are issued via menus, control-key sequences, and mouse movements). vim, at least when it initially starts, doesn't know about mice, menus, etc. I suspect you are asked to edit "rt61sta.dat" with vim rather than gedit because "rt61sta.dat" needs to be treated as binary, and perhaps gedit isn't able to do that. A few crucial vim commands you'll need include...

Use the arrow keys to move the cursor around in the file.

:h (the two-character sequence colon followed by h) shows you a help file

i (the single character i) puts you in "insert mode" -- anything you type in insert mode will be inserted into the file at the cursor. To exit insert mode, press the escape ("esc") key.

x erases the character under the cursor (remember it as x-ing out text)

:w (the two-character sequence colon followed by w) saves your edits (remember it as writing your changes to disk)

:q quits vim

You can probably do everything you need with these commands, although there are some shorter ways to do some of it as you get more experienced with vim. If you have a random text file lying around, try vim out on it for a few minutes before tackling "rt61sta.dat".

 
As for what to do once you've got "rt61sta.dat" open in vim, the "readme" file that step d of your directions refers to is the key. This file should be in the directory to which you untarred the rt61 module from RaLink. The last 3/4 of it or so are an explanation of "rt61sta.dat". This explanation starts by showing you a sample file (which will be very much like what you see initially in vim). The file is essentially a series of parameter settings for the rt61 module. The "readme" file also has a parameter-by-parameter explanation of these parameters and the values they can take on.

Good luck!

---

### Post by gatoruss on 2007-05-31
Thank you, Doug.

After tinkering, I have gotten the wifi to work following the tutorial mentioned above...thing is I cannot get it to fire up on start up...I need to manually launch every time I boot up?"

I tried to set up a start up script in the manner described in item (g) of the following link: [http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980); as modified per the Additional Notes, item "(c) "No DHCPOFFERS Received."  But it does not fire up wifi on start up....any suggestions?

---

### Post by DougB1958 on 2007-05-31
Well, I start my wireless on startup via "/etc/network/interfaces", so I don't have any experience with the script mentioned in the thread you cite. The relevant lines in my "/etc/network/interfaces" file are
```
auto ra0
iface ra0 inet dhcp
  pre-up iptables-restore </etc/iptables.up
  wireless-essid abcdefg
```
where "abcdefg" on the last line is replaced by the actual ESSID for my wireless network.

As I understand things, the line "auto ra0" is the one that indicates that the wireless interface is to be started on system start-up. The line beginning "pre-up" sets up my firewall; if you don't use "iptables" for a firewall you don't need it.

Prior to upgrading to Feisty, I was using the driver downloaded from RaLink, much as the thread you're following recommends (except that the driver was easier to compile prior to Fesity). I used the stanza above in "/etc/network/interfaces" to start my wireless in those days (and still do, except now it also runs the script I described earlier in this thread). Don't know if this will help you, though, or whether you're better off asking for ideas on the thread you've been following. Good luck in either case.

---

