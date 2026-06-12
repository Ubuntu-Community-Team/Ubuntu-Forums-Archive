---
title: "wvdial in Ibex"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by JPman on 2008-12-28
****I've never had any trouble before setting up my dial modem but Ibex seems to think all there is in the world is networks and Wireless.    It's bad enough to be pushed onto the back burner by the local phone company and alternative ISP access providers who ignore Linux in favor of M$ and Apple but now Ubuntu is ignoring all of us who are stuck with dial up.

I can see by searching my local package manager that wvdial is installed in Ibex and I followed the instructions to configure it but though the directions explicitly refer to "dial up modem" the setup program leads me to another damned network dead-end.   The menu reference does not exist in Ibex though it did in Heron.    I am supposed to go to sys,admin,net...    No such animal.  There is sys,admin,network tools but this is all about networks.

I don't have any network, wireless or multi-users.  It's just one guy with a telephone modem.  Basic.  Simple.  Should be easy.

Why, oh why can't you folks have left wvdial alone?    Why did you do this?    So simple it would be to leave a menu item for modems.    So easy but without it I'm screwed.    Shall I go back to the hated XP or what?

Someone in Ubuntu engineering seems to think that dial up is history and needn't be bothered with anymore.    How cavalier of them!

So I've been an Ubuntuer for a couple of years now and looks like the end.    I should not have to work a console for something as essential and basic as modem config.    Don't have to in XP!

Any suggestions that won't have me doing console back flips or should I change to another Linux?

Someone please forward this message to Canonical engineering staff.    I feel they need to know about the trouble they've caused so many of us.
:(

JP Simmons, just about to move to SUSE.   They still support modems.**[B][B]**[/B][/B]****

---

### Post by Shazaam on 2008-12-28
What kind/brand/chipset modem? I use dialup with an internal Conexant chipset winmodem and once I got the hcf drivers installed it was a breeze connecting with wvdial. Then I was able to install gnome-ppp to simplify everything.

---

### Post by JPman on 2008-12-28
My modem and drivers have always been detected before by Ubuntu.   The problem now is getting Wvdial to do anything.    How did you manage that with no menu selection?   All the menus have to do with networks and wireless, not pots modems.

How did you config your modem?    Menu?   Console?   How?   Did I miss something?

---

### Post by Shazaam on 2008-12-28
Had to use the cli (console), they took out the dialup section in Network Manager.
Open terminal, enter...
```
gksudo gedit /etc/wvdial.conf
```
and add your info...
```
[Dialer Defaults]
Phone = 
Username = 
Password = 
New PPPD = yes
```
Save it. Then open terminal and type in...
```
wvdial
```
Keep the terminal open as long as you need to be connected. To disconnect either close terminal or hit Ctrl+C.

---

### Post by Michaelg14 on 2008-12-29
You might also get wvdial to configure itself if you enter

```
sudo wvdial
```

with your modem connected.

You still need to enter your dial-in number, username and password but it will detect the init string required on some modems.  If it doesn't no harm done.

---

### Post by GuyK on 2008-12-30
I've gone this route and get an initilization failure saying couldn't find valid number, name, and password. wvlanconf recognizes my ext. modem OK.

I can't do any wireless from home location and need to have functional dialup. I've installed kppp (for use with Kubuntu dual-desktop option) and it hangs up in the process of configuration. (The dual desktop feature isn't working right either) Woe is me!

I would appreciate help in getting dialup up

Guy K

---

### Post by Michaelg14 on 2008-12-30
I am posting the contents of my wvdial.conf.  I don't know if it will help but maybe you can adapt some of it to work with your modem.  Use ```
gksu gedit /etc/wvdial.conf
```

```
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = #777 (for Verizon broadband only)
Modem = /dev/ttyUSB0
Username = *************
Password = *******
Baud = 460800
```

Hope that helps

---

### Post by cebobbitt on 2009-01-02
Have you tried pppconfig? Its a cli program, but it is very good. I usually get my dial-up working with it first and then go and install gnome-ppp, which is a frontend for wvdial.  I usually keep both around, it is not a bad idea to have more than one backup, hee hee!! Yepper, I hope this helps.

---

### Post by cek on 2009-01-02
Open a terminal.

type:

sudo wvdialconf

type:

sudo gedit wvdial.conf

Edit user name, password and phone number as described above, save.

type:

sudo wvdial

You are now connected.

Open another terminal.

type:

sudo apt-get install gnome-ppp

Now you have the GUI program GnomePPP (a very simple front end to wvdial).

---

### Post by malspa on 2009-01-10
> **cek said:**
> Open a terminal.

type:

sudo wvdialconf

type:

sudo gedit wvdial.conf

Edit user name, password and phone number as described above, save.

type:

sudo wvdial

You are now connected.

Open another terminal.

type:

sudo apt-get install gnome-ppp

Now you have the GUI program GnomePPP (a very simple front end to wvdial).


Does this work ok in 8.10?  Haven't tried it here yet, just asking.

---

### Post by Michaelg14 on 2009-01-13
AFAIK 8.10 doesn't use wvdial.  I have a CDMA modem that used wvdial in 8.04 but in 8.10 it is not needed.

---

### Post by niteshifter on 2009-01-13
> **malspa said:**
> Does this work ok in 8.10?  Haven't tried it here yet, just asking.

It's going to be trouble in any version. The error(s):

```
sudo gedit wvdial.conf
```

Followed by
```
sudo wvdial
```

Will get you problems. Minor error with first: use gksu. The major error is wvdial looks for /etc/wvdial.conf unless you tell it otherwise. So after making wvdial.conf in /home/<username> we have wvdial using the one in /etc.

If you edit /etc/wvdial.conf then all users that have permission to use wvdial will be using the one configuration. It's system wide:
```
gksu gedit /etc/wvdial.conf
```

If you wish each user to have their own configuration then of course wvdial.conf needs to be in that user's home folder. Users then invoke wvdial like this:
```
{sudo} wvdial -C wvdial.conf {section}
```
Where
{sudo} is optional - not needed if you've set permissions (as in user in group dialout or by editing sudoers).
{section} is optional - not needed if ~/wvdial.conf is headed with [Dialer Defaults].

Also, if invoking with -C then the file name doesn't have to be wvdial.conf, call it what you like.

---

