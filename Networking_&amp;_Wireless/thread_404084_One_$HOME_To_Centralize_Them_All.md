---
title: "One $HOME To Centralize Them All"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by dfm21 on 2007-04-07
Hi!

Wherever I am, I want the same home environment - be it at home on my desktop or notebook machine or away without connection to my LAN server.

I better explain:
At my university, you can log in from any machine and see the desktop as you left it (it works with both gnu/linux and windows). This is probably done with a Samba PDC, some backup servers, whatsoever. I could implement a similar architecture here at home, but it would take loads of time and, after all, be too "heavy" for my needs.

At the moment it would be enough if my Ubuntu stations, i.e. Desktop and Notebook, were "in sync".
I have a small home server (Ubuntu Edgy LAMP) where I store files and run [hellanzb]("http://www.hellanzb.com/trac/").
To centralize my user environment I could make both clients mount their home directory from the server (the same for both):
```
mount -t nfs /media/server/home/me /home/me
```
I did not try this because of two problems:
1. What if my desktop PC and my notebook write a file simultaneously?
2. When I am away and offline I can not mount /media/server/home/me, so I would need an offline copy on my notebook.

Maybe the first one is no problem at all... You can log in with different shells and modify the same file without problems (locking).

But the "away-and-offline case" keeps bothering me. Maybe a simple bash script could help that checks if the server is available and if so mount the server's home or else mount the last copy of the server's home. Though, if I write files while being away, they would have to find their way back to the server somehow.


I hope this text is readable (English is not my mother tongue) and somewhat understandable.

Keep this distro what it is - the best!

Felix

---

### Post by dmizer on 2007-04-08
well, here's going to be part of your puzzle: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

the above link has directions on how to mount a separate home directory, which is going to be something you'll need to do.

the same home directory will be relatively simple to accomplish over a local network.  but will likely be extremely difficult to accomplish on a remote system.  also, you won't be able to share the same home directory across two computers if they are both signed in at the same time.

the way i've solved this issue is by carrying around my home directory on a usb hard drive.  it's an old 40 gig drive i yanked from a broken laptop.  i have to make sure that the usb drive is pluged in before i boot the machine, and i had to make changes in the boot order to make sure usb was mounted before the home directory was needed.  otherwise it works fairly flawlessly.

i do have problems sometimes during updates, on which occasion i remount the original home directory for the given machine before performing the update.

it's actually a fairly complex arrangement, but it is convenient.

remember though ... if you mess things up, your computer will not boot.  keep us posted if you decide to make this work.

alternatively ... you could set up a thinclient: [https://help.ubuntu.com/community/ThinClientHowto?highlight=%28client%29%7C%28thin%29](https://help.ubuntu.com/community/ThinClientHowto?highlight=%28client%29%7C%28thin%29) which might be better suited to your needs.  you'll essentially end up with your laptop and desktop being terminals and your entire configuration is stored on a central server.

---

### Post by dfm21 on 2007-04-12
Thank you for your ideas, dmizer!

I will keep you posted if I make any progress with that.
A thin client solution would not be what I want as the the computing is done on the server - though my desktop is the power machine and my server is... well.. slow. ;)

I know there is a way to make this good - it just lies behind some bushes. I need a machete.

btw: Thanks for the link in you signature to the  "Linux is not Windows" article! I enjoyed reading it.
Maybe you find these interesting:
[http://www.gnu.org/gnu/gnu-users-never-heard-of-gnu.html](http://www.gnu.org/gnu/gnu-users-never-heard-of-gnu.html)
[http://www.gnu.org/gnu/why-gnu-linux.html](http://www.gnu.org/gnu/why-gnu-linux.html)

so long

---

