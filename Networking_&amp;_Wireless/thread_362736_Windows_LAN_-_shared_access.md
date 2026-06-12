---
title: "Windows LAN - shared access"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by rrand on 2007-02-16
G'day,

I have installed Edgy Eft as a dual boot with Win2k and it went ok.  I can access the net fine in Ubuntu via a win2k gateway on my 3 pc wired LAN which was pretty simple once I got my addresses sorted out.  I can ping the other two systems from Ubuntu ok and vice-versa.  But because I am a dumb newbie I am unable to work out how to get access from Ubuntu to shared folders on other 2 windows systems and vice-versa. All I have been able to achieve with various options (via Places - Network Servers etc.) is a Desktop Configuration file called Windows Network and an empty folder for each of the win pc's.  I have read so many posts and docs I am going round in circles.  I think I need Samba and probably something else - maybe a new brain would help.  Any assistance would be greatly appreciated!

---

### Post by gradedcheese on 2007-02-16
Hi.  Yes, Samba is what you need.  Make sure it's installed:

```

sudo apt-get install samba-client

```

Places->Network Servers does indeed allow you to browse, though it can be a little flaky.  Press 'refresh' in the file browser and try it a few times, the Windows Network folder should eventually show your servers :)   If not, try this: look up the "name" of the PC you want to connect to and then select Go->Location and type in:

smb://name_of_pc_here/

If that doesn't work, look up the PC's IP address instead and do the same thing, putting the IP where the name goes.  Note that it's two slashes after "smb:" and not three (which Nautilus likes to put in sometimes)

---

### Post by dhoodle on 2007-02-16
Hello,
I am a complete ubuntu/linux newbie.  I am in the same predicament as [COLOR="DarkOrange"]**rrand**[/COLOR].

I attempted to install samba with the code that [COLOR="DarkOrange"]**gradedcheese**[/COLOR]. posted:
```
sudo apt-get install samba-client
``` and received this error:
```
dhoodle@dhoodle-laptop:~$ sudo apt-get install samba-clientReading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba-client is a virtual package provided by:
  smbclient 3.0.22-1ubuntu4.1
You should explicitly select one to install.
E: Package samba-client has no installation candidate

```

any ideas on what to do ?

I have a Windows PC - and now this Linux Laptop - I love the GUI, and am sick of the MS monopoly on everything - sick of windows...  Alas - I will always keep my main PC windows - that is of course until/when I am completely confident and satisfied with Linux.

So i need to get these 2 machines networked - they were networked before I installed Linux on this machine, with the XP network wizard.

Any help would be great!

Thanks in advance!

dhoodle

---

### Post by gradedcheese on 2007-02-16
you can run:

```

sudo apt-get install smbclient samba samba-common

```

to install smbclient, which turns out to be the real package name.  I am not 100% sure that you actually need this though, I guess there's something else that ubuntu ships with that handles samba browsing?

You can also read this [very basic guide]("http://andrey.thedotcommune.com/samba.html") I wrote about setting up Windows networking (from the Linux side)

There's nothing earth-shattering there, just some notes about setting up shared folders (with user permissions as needed).  That should be enough to get your two PCs talking to each other.  You will need to use the shell a little bit, but hopefully you'll find that kind of fun :)  When I say "edit a file", you can do so with the graphical gedit editor.  For example:

```

sudo gedit /etc/samba/smb.conf

```

opens /etc/samba/smb.conf with gedit using sudo.  Ignore any warnings that get show in the shell (they are normal) when you run this.

---

### Post by dhoodle on 2007-02-16
Thanks for that [COLOR="DarkOrange"]**gradedcheese**[/COLOR]
I will give it a hit in a moment - am receiving this message now....
```
sudo: timestamp too far in the future: Feb 17 08:48:55 2007

```

I adjusted the time manually, and since then this error has been occurring.... any ideas ?

:lolflag: I am a total and utter newbie at Linux - it took me 10 mins to find the terminal.... haha

---

### Post by dhoodle on 2007-02-16
hey mate - fixed that issue - just updated the internet time...

---

### Post by dhoodle on 2007-02-16
Thanks heaps mate - done it... - I can see them in linux - my shares and the windows shares, but when I go in to windows I cannot see anything ?

---

### Post by KAL9000 on 2007-02-17
I thought id just add to this, Ive got the shared folders set up btu when i try to access the system from my windows laptop is prompts for a user name and password. Ive tried my Linux login and it does nothing and the laptop doesn't have a password set for windows. what is it asking for?

---

### Post by gradedcheese on 2007-02-17
KAL9000 -- you need to add youself via smbpasswd and restart samba, I have an explanation toward the middle of this page:

[http://andrey.thedotcommune.com/samba.html](http://andrey.thedotcommune.com/samba.html)

namely:

```

sudo smbpasswd your_user_name
sudo /etc/init.d/samba restart

```

---

