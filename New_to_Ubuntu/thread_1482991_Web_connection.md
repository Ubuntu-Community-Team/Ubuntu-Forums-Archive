---
title: "Web connection"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by Dsoslglece on 2010-05-14
Hi,
I've just intalled Ubuntu in a partition on my iMac-Intel, and managed rather easily to install it and let everything work without problem (it seems very intuitive) except for one or two things that are still unresolved. One of those, I already mentionned in a previous post, but now there is this new question of connecting to the net with a browser.

**First thing, my config:** 
On iMac, I idn't install it with bootcamp (that obliges one to stop Snow Leopard before to boot Ubuntu or XP pro or win7) but using Parallels desktop, that allows one to have few systems running together on different virtual screens, and to navigate and exchange whatever one likes from one to the other.

**Now, the problem:**
Just after the install of Ubuntu, connecting to the net with FireFox was fine, I could go anywhere, and download anything.
Then, after a day or two, each time I tried to connect with FireFox, it said the connection was off; same thing with Arora. And I couldn't even install programs from the logiteck, it also said the connection was off.

* So, _I verified from Snow leopard, using my main browser_ (FireFox), and there was no problem, everything works fine.
* I also then verified if anything was maybe _visible on Parallels desktop menu_, indicating some filtering or connection *on* or *off*, but nothing.
* I verified if everything was properly _set up in the Mac firewall_, but normally, every system installed with parallels desktop goes out using parallels desktop permissions.
* Same thing with _Little Snitch_ (a sort of firewall for outgoing flows)
* I then went to the _router_ of my LiveBox (my ISPs modem), and looked if everything was OK, (I generally remove anyway as many protections on there as possible : firewall and antiV, mostly for windows users, since I have what is necessary on my machine), and it was OK.
* So, I verified with _xp pro_ (already installed on there), and from this system, FireFox had no problem. the same with _Windows7_.
* I then tried with a version of _Kubuntu_ already installed on here, and there was also no problem.
* So, next step, I installed a _second version of Ubuntu_ and started it, and then, I could again connect to the web ! So fine, I planned in a near future to delete the previously installed Ubuntu...

It went OK for a while, but today again, no connection from Ubuntu.
All other systems can connect without trouble (using FireFox, Safari, Konkeror).

So, I have the proof now that the stops _can only come from Ubuntu_.
Is there maybe something in it to be programmed, for example to stop connetion after some time (for instance for kids), sort of a filter getting automatically in the way for some reason?

On the first install of Ubuntu, I did install Vidalia with polipo, but when verifying all, I uninstalled it completely, so, it can't be it (and I also verified that the setup in FireFox prefs are on NO proxy).

I'd be very obliged if someone had an idea about this… Thanks in advance

---

### Post by 3rdalbum on 2010-05-14
I don't know why this would be so, but it's possible that your virtualisation software is no longer passing DNS entries through correctly to Ubuntu. You could try this little HOWTO: [http://www.chrislees.info/ubuntu/opendns.shtml]("http://www.chrislees.info/ubuntu/opendns.shtml")

Also, you probably already know this, but don't try to install Ethernet or wireless drivers inside Ubuntu when it's in the virtual machine.

---

### Post by Dsoslglece on 2010-05-14
Hi, and thanks for your answer.
It looked promising, but doesn't seem to work…
I went following the link, and then did what was advised to do:[SIZE=4][COLOR=Blue]
[FONT=Georgia]System > Preferences > Network Connections[/FONT][/COLOR][/SIZE]
and, in there, after choosing "automatic only", added the DNS address of my ISP, and its domains research name. But it doesn't seem to want to register, since the button "register" is grayed out, and the only one alive is "cancel". I thought that maybe I had to add routes (they seem to ask for it), but if I entered the 3 first addresses (IP, Router, etc) I can't work out what is the last one (metric?), and so, even if that is filled up, it may not be enough. 

I also tried with the DNS address given on this post, but it produces the same result.

However, I don't think to remember having seen anything in this window (Network connections) for the other systems (or earlier for Ubuntu, when it was working) but I will verify… since normally, the connections are established through Parallels desktop, and not directly toward the ISPs server.

Anyway, thanks, and I'll continue to search, since the matter is not closed yet !:)
[SIZE=4][COLOR=Blue]






[/COLOR][/SIZE][/FONT][FONT=Georgia, Arial, 'Times New Roman', Times][/FONT][FONT=Georgia, Arial, 'Times New Roman', Times][/FONT]

---

### Post by Dsoslglece on 2010-05-16
Hi, 
I bet the problem is now resolved, since I'm using Ubuntu's navigator to post on here !
It had been possible earlier though, but anyway, and since it could be of some benefit to someones, here is what I did.
First, and since every time I had installed Ubuntu, the connection worked for a while, I decided to install it once again, and, this time, with security ropes around it, so, just after the install, I did a snapshot of the system, and another one just after customizing it.
But also, I went to the file: "Web connections", and realized that some data were there that weren't on the late other system: for instance, in the window Editing <name of the connection>, in the tab "Wired", there was a MAC address... I still have to find which: I'm sure it is not the one supposedly of my system visible from the net (that I change as a rule with ChangeMAC), nor the real one, so maybe it is related to Ubuntu... but anyway, and this is the most important, it was found automatically each time, and now, even if it somehow would disappear, I took a copy of it and can write it back on the right place (and of course, as a last resort, use a snapshot!).

---

