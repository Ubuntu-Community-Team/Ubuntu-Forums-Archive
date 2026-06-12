---
title: "Struggling with internet - lost wifi"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by b1llyboy on 2010-05-25
Hi all:

Got some problems connecting to the internet through wifi (I'm using Lucid 64 bit).
Things were working till last night, but internet was slow (about 200Kb/s compared with 2x that in Windows and was faster still in Karmic). I had disabled IPv6 as in other posts, and it did help a lot, but internet was still crawling relative to to other OSs).
Last night I read a post that suggested setting the router to bridge and running ppoeconfig. Tried this and lost all connectivity, so I reset my router to normal and everything seemed to be fine.
Then, this morning, I found that I could not contact my wireless router using Linux. I still get asked for the password to the keychain, but the Network Manager icon does not appear.
I've assumed so far that the problem involves an inability to access my USB wireless adapter (a DLink) because of the lack of a Network Manager icon, but am not sure that this is the case. (USB is working fine).
The wireless adapter is okay, as is the router (they both work under windows) but I can't seem to make any headway with this in Ubuntu at all.

Any thoughts on how to resolve this very much appreciated. Could it be something really silly like Network Manager somehow being turned off, and if so does anyone know how to turn it back on?

Thanks,

Billy.

Quick update - I can get the Network Manager back by typing:

sudo killall NetworkManager

I guess it restarts, but it says my wifi is not managed. If I try nm I get

(nm-applet:1973): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager

---

### Post by SRST Technologies on 2010-05-25
Christ this is getting annoying.  Amateur hour is in full force on this forum anymore and it makes me sick sometimes.

Just how the hell are you supposed to bridge a ppoe connection from the router over the wireless to a wireless device when, if you put any router I've ever heard of into bridge mode, it deactivates the wireless device on the router?  It's hard to perform a pppoeclient connection to a wireless router when you SPECIFICALLY TURN THE WIRELESS OFF.

In the future, you have to remember something... there's been a hellish influx of people who have had Linux for thirty minutes so they think it makes them qualified to answer intricate questions regarding a host of topics they've never heard of and have never worked with before.  I just got done answering a question a few minutes ago where some guy literally chimed in that he'd never used or configured Samba before but he likes it.  How does he know if he likes it, he's never used or configured it before!

You may want to start researching the posting history of the people giving you answers to see if they've ever actually helped anyone before or if anything they've ever said even remotely fixed a problem.  Most of the guys on here giving the kind of advice you just got get rebuffed on a constant basis by people who actually know what they are doing.  Evaluate both the advice given and who is giving it.

On to your actual problem.

You're getting the DBUS error because even though you are killing off network-manager with killall it is not stopping the program.  network-manager (nm) has some special configurations to it that cause it to reopen after a killall much like killall gnome-panel reopens the panel after it gets killed.

I do not know the elegant solution to this problem, but I do know how to fix it.  Try this.  I hope you have an ethernet cable you can use for about ten minutes.

Connect to the ethernet port of your router (and I hope it isn't still in bridge, but you did say you took it out of bridge mode).  Open a terminal and copy and paste the following command.

sudo apt-get purge network-mananger network-manager-gnome

Reboot.

Go back to the terminal and copy and paste the following command.

sudo apt-get install wicd wicd-gtk

Reboot.

Open a terminal and copy and paste the following command 

sudo apt-get purge wicd wicd-gtk

Reboot

Open a terminal and copy and paste the following command

sudo apt-get install network-mananger network-manager-gnome

Reboot.

After this last reboot, all should be well.  I know it seems a little odd to install and then immediately remove all the wicd stuff, but for some reason if you just purge the network-manager goodies and reinstall it doesn't do any good.  Something in wicd is resetting the network-manager settings that even a purge cannot do.  I don't understand it, but it works.  When you reboot the last time, you should be able to disconnect from the ethernet port of your router and use wireless again.

Good luck!

---

