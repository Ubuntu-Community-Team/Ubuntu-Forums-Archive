---
title: "Random Disconnects with BCM 4318"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by halberd25 on 2007-02-21
I'm new to Linux, but let me tell you, I like it a lot already.  I have broadcom 4138 wireless card in my laptop, and I got it to work, but occasionally it will disconnect from my network and I can't get it to reconnect.  Furtermore, most of the time when I start Ubuntu, it will be disconnected and I have to edit the configuration, and add a DNS or host for it to work again.  I honestly am not completely sure what makes it work again, but I usually can get it to work.  I have wireless assistant downloaded, but it's not much help.  Does anyone have any ideas on how to fix this?

---

### Post by Floppyjoe on 2007-02-21
Do you connect with dhcp or static IP? If you connect with dhcp and find that your DNS settings get rewritten then this may be a solution for you:
> Basic Instructions

Please write down your current DNS settings before switching to OpenDNS, in case you want to return to your old settings for any reason.

The DNS Server addresses for OpenDNS are:

    * 208.67.222.222
    *
    * 208.67.220.220

Just add these two lines somewhere near the top of your /etc/resolv.conf:

nameserver 208.67.222.222
nameserver 208.67.220.220

Enjoy!
Using OpenDNS with DHCP

If you assign your computer's IP with DHCP, it probably overwrites your /etc/resolv.conf. Here's how to fix that:

   1.

      Run: sudo gedit /etc/dhcp3/dhclient.conf
   2.

      Change the prepend line to read:

      prepend domain-name-servers 208.67.222.222, 208.67.220.220;

      This will prepend the OpenDNS addresses to the top of the list. (You can also use "supersede", which will just use them.) You don't have to worry about the DHCP client overwriting settings on each reboot or lease cycle, and your ISP nameservers will still be used as backup.
   3.

      Run: sudo /etc/init.d/networking restart
   4. Using Ubuntu? Check "Networking" to see if the changes applied correctly.
      Go to "System –> Administration –> Networking" and click the DNS tab.


Hope this helps
Floppyjoe

---

### Post by halberd25 on 2007-02-21
I'm not sure if it helped.  The internet locked up again, so I restarted my computer.  It seems like every time I restart, it hasn't saved the settings I've used and I have to fanagle with it to get it to work.

---

### Post by halberd25 on 2007-02-21
No, it's still really inconsistent

---

### Post by Ryzzen on 2007-04-24
I have the same problem. I'm assuming this is with Feisty, right?

I can get about 10 minutes of internet use before it disconnects. It'll still show my wireless network, but I won't be able to connect to it. I switch to manual configuration and set it up that way, but it does nothing. And it's impossible to switch it back to automatic once I do manual.

Ctrl + Alt + Backspace doesn't fix it, but rebooting my computer does. It also resets Network Manager back to automatic, and will work again for approximately 10 minutes before disconnecting. Rinse, repeat.

Also, that annoying Keyring thing pops up every time I boot and asks for my password to connect to the wireless connection. Not the WEP key, the random password I made up to make the Keyring window go away.

The signal strength is a lot lower too. I use it in the room next door to my router, and it was always at 90-100% in Edgy without Network Manager. Now it fluctuates between 25-50%.

This is extremely disappointing, since wireless was supposed to be *improved* for Feisty, when in fact it's worse than Edgy...

(I have a Compaq v2410us with a Broadcom 4318.)

---

### Post by halberd25 on 2007-04-24
After I installed ndiswrapper, it doesn't do it anymore.

---

