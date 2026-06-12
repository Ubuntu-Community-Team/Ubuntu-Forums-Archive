---
title: "Noooobie Frustration w/Wireless Results in Insanity!?"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by ByteTraveler on 2008-02-28
Yes, I'm a Nooobie to Ubuntu, but am  computer savvy (I develop LAMP apps at work on Redhat boxes maintained by a consultant).

But, this is my first Linux install @ home.

I've gotta say. the Ubuntu desktop install was smooth as silk, and I was connected (wireless), getting updates, and on the web, within 10 minutes.

I was about to jump for joy, and proclaim this better than the Windows world I was planning to leave, when I discovered that I had to enter my wireless router's WPA key every single time I booted!!!!???

I have to say, I installed a Vista box about a week ago, and it featured intuitive, "Make this my default network," and "Remember my password" checkboxes.

That just seems like "common sense" - If you're going to design a wireless GUI interface, and you spend 20 seconds thinking about it, "Make this my default network," and "Remember my password" would rank-among the top-two requirements (or, so it would seem).

I have (literally) spent the last two hours Googling solutions... A myriad of cryptic posts (assuming I'm a Linux guru), have ranged from suggestions to "Check remember my password" (there is no such prompt), to convoluted gyrations requiring the download of packages, and the editing of config files (none of which worked). I even did a full reinstall, and followed the steps in the sticky note here, and nothing...????

I'm still prompted for the WPA key every single time I boot.

Wireless in Ubuntu works perfectly if I'm in "roaming" mode, and manually provide my WPA key each time, but it's useless when I want my key memorized.

OK - I'm very tired & frustrated, but who, in their right mind, would build such an otherwise cool wireless interface, and "forget?" (whoops) to include, "Make this my default connection," and "Remember my password?"

I mean, even Microsoft Vista thought that one through a lot better.

Again - Sorry for "venting" (and my frustration), but can someone please guide me towards the (seemingly basic) "Make this my default network," and "Remember my password" in wireless?.... I've spent hours with this, and would like to go to bed.

---

### Post by dynamethod on 2008-02-28
The below is an excerpt taken from: [http://ubuntuforums.org/showpost.php?p=2395871&postcount=1](http://ubuntuforums.org/showpost.php?p=2395871&postcount=1)

But this should work for you

Try this:

   1.  Edit the /etc/network/interfaces file
      Code:

      gksu gedit /etc/network/interfaces (if you are using Ubuntu)
      kdesu kate /etc/network/interfaces (if you are using Kubuntu)

   2. Look for a section containing "wlan0"(or whatever your network interface is), if there is no such section, add the following to the bottom of the file:
      Code:

      auto wlan0
      iface wlan0 inet dhcp

   3. Beneath those lines, add the following (*):
      Code:

      	pre-up ifconfig wlan0 up
      	pre-up iwconfig wlan0 essid YOUR_ESSID
      	pre-up iwconfig wlan0 key WEP_KEY_OR_"OFF"_IF_YOU_HAVE_NONE

   4. If you have it installed (you will if you are using dapper), remove network manager (!)
      Code:

      sudo aptitude purge network-manager


If you have an ASCII wep key, make sure to prefix it with an "s:" (without the quotes). There should be no white space between the semicolon and the actual key. If the key is shared you need to add "restricted" (again without the quotes) directly after the "key" part. Make sure to seperate "restricted" with a space on either side of the word. Thanks to NewWithoutClue for pointing this out.

If you are using WPA security on your wireless network, then your /etc/network/interfaces file should look like this:

Code:

auto wlan0
iface wlan0 inet dhcp
    pre-up ifconfig wlan0 up
    pre-up iwpriv wlan0 set AuthMode=WPAPSK
    pre-up iwpriv wlan0 set EncrypType=TKIP
    pre-up iwpriv wlan0 set WPAPSK="YOUR_WPA_PSK_KEY"
    pre-up iwpriv wlan0 set SSID="YOUR_SSID"
    pre-up iwpriv wlan0 set NetworkType=Infra

---

### Post by ByteTraveler on 2008-03-13
Thank you for trying, dynamethod, but...

When I tried the first edits, "Keyring" (I don't want to know what that is) wanted the root password to save the changes.... Another hour-or-so of Googling gave me some hints about why Ubunto doesn't establish a root password (I was never asked during install), and how to work-around that, and even if I had the energy to investigate that, the rest of your message was just.... Too much.

I just want to boot, and use Linux.

Is there someplace I can check "remember my wireless key, and log me in?"

---

### Post by ByteTraveler on 2008-03-13
> **dynamethod said:**
> 

If you are using WPA security on your wireless network, then your /etc/network/interfaces file should look like this:

Code:

auto wlan0
iface wlan0 inet dhcp
    pre-up ifconfig wlan0 up
    pre-up iwpriv wlan0 set AuthMode=WPAPSK
    pre-up iwpriv wlan0 set EncrypType=TKIP
    pre-up iwpriv wlan0 set WPAPSK="YOUR_WPA_PSK_KEY"
    pre-up iwpriv wlan0 set SSID="YOUR_SSID"
    pre-up iwpriv wlan0 set NetworkType=Infra

The more I researched this, the more this looks like the solution, but I (literally) can't... Ubuntu tells me I don't have permission to save the file, and we're back to that whole mystery about what the root password is (which I've also been Googling for days).

<laughing>.... There *HAS* to be something I'm really missing here... I dread the Gates/Ballmer stuff, but have to admit, I was up & running with Vista on my other box in about 15 minutes - They had a "remember me, and log me in" check-box.

I've been at this (Ubunto) for more than a week.

Forgive me for my frustration, and thank you for your patience.

---

### Post by acirilo on 2008-03-13
before you start to edit the file type "sudo" without the quotes 

it will prompt you for your own password then you will be able to save the file after editing it...?    or maybe not... i'm to new at this linux also

---

### Post by Integration on 2008-03-13
gksu gedit /etc/network/interfaces
then enter the administrator password that being your password if you only have one account.
Then on the text editor enter the code and save:

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="YOUR_WPA_PSK_KEY"
pre-up iwpriv wlan0 set SSID="YOUR_SSID"
pre-up iwpriv wlan0 set NetworkType=Infra

---

