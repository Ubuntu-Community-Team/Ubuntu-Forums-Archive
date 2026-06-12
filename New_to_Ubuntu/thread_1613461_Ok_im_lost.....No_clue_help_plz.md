---
title: "Ok im lost.....No clue help plz"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by theshavenape@hotmail.com on 2010-11-04
Mythbuntu:

New to linux never used it on the gorunds of i cant play my pcs games on it so never botherd now i have media pc using mythbuntu.

Problem are as follows.

USB dvd drive worked to instal but now it wont reconise it to play dvds. I have no concept of how comand codes work etc so any advice english only plz i dont speak leet or geek :P

i have a tv dongle on way 

Hauppauge WinTV Nova-TD Diversity USB Stick with Dual DVB-T Tuner

what hoops am i going toi have to jump through to make this work ei record and watch tv and operate sytem via the remote. I picked Hauppauge because it seems to be the preferd brand on the forums i looked at 

Ty in advance for any help you can offer or its windows 7 and media player..........Not a journey i want to take.

---

### Post by Zzl1xndd on 2010-11-04
Do the DVDs load and not play or does the system not recognize the DVD's at all when you put them in?

---

### Post by Cobracommand0 on 2010-11-04
I've never used Mythbuntu, but as far as getting DVDs to work you probably need to get the restricted-extras and libdvdcss2 packages.

Open up a terminal and run these commands:

```
sudo apt-get install ubuntu-restricted-extras
```Then

```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```Then

```
sudo apt-get install libdvdcss2
```You might want to refer to this page for the overview of this process:[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository)

---

### Post by Koppie on 2010-11-04
Welcome to Linux!  Thanks for asking for help.  You're on the right path.

For DVD, you need Ubuntu Restricted Extras.  Here's how you get it:
1. Exit Myth
2. From the Ubuntu desktop, go to the Applications menu (upper left corner), and select Ubuntu Software Center (last item on the menu)
3. Search for Ubuntu Restricted Extras (search box is upper right corner)
4. Install it.  You'll need to enter your password.
5. Restart the computer (probably don't need to but it couldn't hurt).  DVDs should work now.

For the TV tuner, looks like you did your homework.  I don't have that tuner so I can't say for sure, but it looks like it should Just Work.  For using TV tuners in Linux, I highly recommend LinuxTV.org.  Here's their page for your tuner: [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500).  It's got lots of technical stuff on it; just try plugging it in first and see if Myth understands it.  If not, then try reading that page and come back here if you need more help.

For what it's worth, I tried doing exactly what you're doing, and got fed up with the Mythbuntu interface.  So now I just use "plain vanilla" Ubuntu with a small program called TVTime.  I've got Hulu, mp3's, DVD, digital cable, and my Wii all plugged in, with 5.1 surround sound output to my amp.  But that's the beauty of Linux: you can do it any way you want!

Good luck and be sure to come back here if you need more help.

---

