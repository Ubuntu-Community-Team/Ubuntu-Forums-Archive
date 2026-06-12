---
title: "Dialup help needed"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by NJC on 2007-03-03
Installed Ubuntu 6.06 to a HP PII/500Mhz Win98 box 256megs. After 4 installs, I at least have the proper resolution and it boots properly. The key to proper video resolution (Matrox Millennium G200 AGP) upon installation, in my situation, was to boot LiveCD using Safe Graphics Mode.

Win98 is C drive; Linux hba (2nd drive) and mirror of drive C is 3rd drive. I "dual boot" by switching the drive boot sequence in the BIOS. 

Question: How can I connect to the internet?? I have configured my modem and internet connection properly but can't find a dialer? I don't have Gnome PPP and running sudo apt-get install gnome-ppp bombs. I see wvdial in the help menu but can't locate it. 

Anyone know of what I can use as a dialer?

---

### Post by dougmorin on 2007-03-03
I can help as much as I can, I am also new but I have had experience with wvdial, so try this and see if it helps.

One thing to remember, wvdial is a command line (no gui) dial-up connection so you will need to run it from the terminal.

Open your terminal and do the following

type in: su - root

it should then ask you for a password, type that in.

then, type in: sudo wvdialconf /etc/wvdial.conf

this should set up the file that you need to connect (the one wvdial reads for information).  You are still going to need to open this file and change a few things though.

in the terminal, type in: gksudo gedit /etc/wvdial.conf, or another way of editing it would be to use: sudo nano /etc/wvdial.conf

make sure you open these as the root user, or else you usually cannot save the files.

Inside the file, there should be three lines...

;Password = <blah blah blah>
;Username = <blah blah blah>
;Phone = <blah blah blah>

Replace the <blah blah blah> part with your information, to look something like

Password = ******
Username = myUser
Phone = 5555555

save and then go to the terminal again and type:  sudo wvdial

this should work, or if it does not you might need to change a couple things in that file.  Let me know if this helps.

---

### Post by NJC on 2007-03-03
Doug;

Thanks very much for your help. It worked! 

I wasn't able to execute the su - root command but all else worked fine. Another question: how are you disconnecting the modem? 

Overall, my connection seems a bit slower in Ubuntu vs Win98 but that could be the extra processor drain of Linux. I need to now figure out how to import Firefox bookmarks and Thunderbird mailboxes/profiles.

---

### Post by dougmorin on 2007-03-04
To close the connection, go to the terminal window that you created the connection and pretty ctrl+c.  This should close it.  I am glad I could be a help to you.

---

