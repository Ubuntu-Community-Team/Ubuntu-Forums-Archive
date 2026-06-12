---
title: "Remotly Accessing an XP computer"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by t-tarzan on 2008-05-08
Hi, i was wondering if i could use my Ubuntu laptop at home, to remote access my XP computer at work. I like to use my home computer to remote access my work computer so i can work from home. This is one of the few reasons i still dual boot with Vista. If someone could tell me if this possible and how to do it, or redirect me elsewhere. Thank you. (sorry for wasting time and space if this question has already been answered.) I am using Ubuntu 8.04 on my laptop and XP on my desktop computer.

---

### Post by helgman on 2008-05-09
Not sure if this is what you are looking for but post #2 might have the answer for you: [http://ubuntuforums.org/showthread.php?t=160183](http://ubuntuforums.org/showthread.php?t=160183)

Regards,
Helgman

---

### Post by jimv on 2008-05-09
[http://www.logmein.com](http://www.logmein.com)

Go there, create an account (free), install it on your Windows box.  Then, when you go home, you can go to the website and log into your XP box.  LogMeIn is platform independent.

---

### Post by MaindotC on 2008-05-09
You can also enable Remote Desktop on your windoze box and use tsclient to connect.  The protocol you'll want to use is either RDP or RDPv5.  If you don't have tsclient installed, type the following in a command prompt:

```

sudo apt-get update
sudo apt-get install tsclient

```

---

### Post by jimv on 2008-05-09
If it's a work computer, he probably doesn't have access to forward the RDP connections through the router.

---

### Post by MaindotC on 2008-05-09
If he has a public address then there's no forwarding and it won't be a problem.  If his work computer is NAT'd then that opens up all sorts of work to do.  OP, do you use public or private addresses at work?

---

### Post by rcmiv on 2008-05-09
This is one of my favorite subjects.  Forgive me if I'm brief, but I'm typing on an eeepc which is... trying.

For connecting from my work (WindowsXP) to home (ubuntu), I use ssh via putty.  A couple of quick googles on putty ssh tunnel should do the trick for you.  Basically, you have to configure ssh-server on ubuntu at home (more googling), and connect with putty from work.  It's command line only unless you use -D and a windows based Xserver like xming. Or install a gui client / server like NX (which is awesome, and free for personal use.)

Connecting from home to work is a different issue, and is problematic for two reasons.  1st, it's technically a little more difficult, and 2nd it's really not a great idea unless your employer is inviting you to do so, and is providing a vpn solution for you.  DIY'g your way into work opens you up to liability if you happen to infect the network from your end.  Not many IT staff that I am aware of are very excited about employees connecting their personal pcs to the corporate network, and most company policies expressly forbid it.

That being said, a fairly simple, and at least supposedly secure way to do this yourself is via Hamachi, which, while closed source, is free for personal use.  I use it to do exactly what you are describing, and have done so for ~2 years without any security problems (knock wood).  Hamachi provides good instructions for setting up the client and server in both windows and linux at their website.  When you get hamachi working, use rdesktop or another linux rdp client to connect to your work (windows) desktop. I was using NX in that direction too, but trust me, RDP is much better (speed, etc).

All of the options I name above are documented excessively on the net, and I figured them all out on my own with nothing but google and a crapload of time, and I am no computer scientist, trust me,   :)

Have fun doing some research, and be as secure as you can.  Don't let someone own your home machine and then bring down your work too.  That'd suck.

-rcmiv

---

### Post by kevdog on 2008-05-09
Hmm, I'm thinking if there is a firewall at work that he couldn't configure, he could create a reverse ssh tunnel from work to his home computer (server running sshd), and then simply tunnel vnc to connect to the work computer (would bypass the firewall restriction).  Wouldn't that be the easiest? If there is no firewall in place, just vnc would do.  Or you could do a nxclient however this is slightly more involved.


What program did you previously use to do a windows to windows connection from home to work?

---

### Post by Go_Bucks on 2008-05-09
I work from home four days a week on all Linux computers while I work for a Windows shop. Whenever I need access to a Windows computer for something (e.g., ArcGIS), I simply use VNC and log in to an available work station.

Of course, whether you can do this or not depends on how large your company is and what power you have. In my case, I work for a small company (eight employees) and I am the second in command. All of the computers at the office (as well as my laptop) are on the same network via hamachi. All of the computers have realVNC installed. When I need one, I find out which one is available and just log in... simple.

---

### Post by CREEPING DEATH on 2008-05-09
Search Synaptic for RDP, I used to have it but I've re-installed a few times since then lol

CD

---

