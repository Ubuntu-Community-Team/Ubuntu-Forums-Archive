---
title: "Almost there on Broadcom card in Hardy"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by Peachpit on 2008-05-07
I upgraded to 8.04 from Ubuntu 7.10 (Gutsy) where I had successfully used a workaround to get my Broadcom wireless card working.
 
   I've spent more than a week trying various ways, found in
users forums, to try and get it working under Hardy to no avail.
 
   But I'm close. I've got ndiswrapper installed (confirmed in connection info box) and Hardy
sees the hardware, tells me the Windows driver (WDM 11)
is installed, sees the network and tries to connect but
never does. Lights are green on the card.
 
   Obviously there's a conflict somewhere (drivers?) but I don't
have the technical knowledge in Linux to find it. I've
uninstalled the cutter(s) I used in Gutsy. But isn't
there something I need to blacklist?
 
   Any suggestions?

---

### Post by GrouchoMarx on 2008-05-08
The following workaround, although unappealing, seems to do the job: [Broadcom Wireless Setup for Hardy (Step by step)]("http://ubuntuforums.org/showthread.php?t=766560&highlight=ndiswrapper+b43")

Step 2 may vary for specific cards, and although step 3 is a little bit redundant, you can do it just to be safe. The key steps are 5, 6, and 7, which unload the native wireless modules at startup (for some reason they load even if blacklisted, necessitating the init script).

---

### Post by Brezhnev on 2008-05-08
I had a similar problem on a Belikn Wireless G card with the  Broadcom 4306 chipset post upgrade to 8.04. I have Wicd 1.4.2 and it reported that no wireless networks were available. Digging a little deeper:

sudo lshw -C network

reported my interface as disabled. A simple reboot cured it. I guess I was lucky.

---

### Post by Ayuthia on 2008-05-08
> **Peachpit said:**
> I upgraded to 8.04 from Ubuntu 7.10 (Gutsy) where I had successfully used a workaround to get my Broadcom wireless card working.
 
   I've spent more than a week trying various ways, found in
users forums, to try and get it working under Hardy to no avail.
 
   But I'm close. I've got ndiswrapper installed (confirmed in connection info box) and Hardy
sees the hardware, tells me the Windows driver (WDM 11)
is installed, sees the network and tries to connect but
never does. Lights are green on the card.
 
   Obviously there's a conflict somewhere (drivers?) but I don't
have the technical knowledge in Linux to find it. I've
uninstalled the cutter(s) I used in Gutsy. But isn't
there something I need to blacklist?
 
   Any suggestions?

Usually the drivers for Broadcom cards for NDISwrapper are bcmwl5.  You might try to see if you can find an XP driver from your PC makers website.  I know that Dell and HP do provide wireless drivers for XP.

---

### Post by SirLawrence on 2008-05-08
> **Ayuthia said:**
> Usually the drivers for Broadcom cards for NDISwrapper are bcmwl5.  You might try to see if you can find an XP driver from your PC makers website.  I know that Dell and HP do provide wireless drivers for XP.

I was able to get the XP drivers from here:
[URL="ftp://ftp.hp.com/pub/softpaq/sp36501-37000/sp36684.exe"]
[COLOR="Blue"]ftp://ftp.hp.com/pub/softpaq/sp36501-37000/sp36684.exe[/COLOR][/URL]

But once the bcmwl5.inf was loaded with ndiswrapper only the drivers would show up and the device present showed nothing.  To get around this I had to create a link from my device (a broadcom BCM4310) to a valid driver in the /etc/ndiswrapper/bcmw5l directory.  After doing this and reloading ndiswrapper my device showed as present!  I rebooted to a blue light and an option to connect to a wireless network!

---

### Post by Peachpit on 2008-05-09
Thanks everyone.

Just got back in town and will try all your suggestions.

Thanks again

---

### Post by kevdog on 2008-05-09
Here is the best link I know -- [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by Peachpit on 2008-05-10
Okay, back again.

I've tried all the suggestions and
nothing has worked yet.

The one that intrigues me the most is
that I'm probably using the wrong windows
driver and that I needed bcmwl5.

I downloaded it but it's a .sys file
and I don't know how to either open
and install it under Linux or to extract
the .inf file so I can use Windows
Network Drivers to install it.

I still think I have everything I need,
just don't know how to put it all together.

I'm probably too old for Linux (57) anyway!

---

### Post by Ayuthia on 2008-05-10
> **Peachpit said:**
> Okay, back again.

I've tried all the suggestions and
nothing has worked yet.

The one that intrigues me the most is
that I'm probably using the wrong windows
driver and that I needed bcmwl5.

I downloaded it but it's a .sys file
and I don't know how to either open
and install it under Linux or to extract
the .inf file so I can use Windows
Network Drivers to install it.

I still think I have everything I need,
just don't know how to put it all together.

I'm probably too old for Linux (57) anyway!

Usually the files come in some kind of .exe, tar.gz, or tar.bz2 format.  Once extracted, they should contain files like:
bcmwl5.inf  bcmwl5.sys  bcmwl564.sys

For .exe files, you can use cabextract to extract the files.  For the other two types, go to the terminal and type "man tar".  It provides some decent information on how to extract them.

You will need the bcmwl5.inf and bcmwl5.sys for 32-bit and bcmwl5.inf and bcmwl564 for 64-bit.  However, to play it safe, I always make sure that I have both.  Once they are loaded, ndiswrapper -l should say driver (xxxx:xxxx) present.  If it says that, it is happy.

Age does not have a factor for Linux.  It is the determination, patience, and willingness to learn!  It looks like you have those three!

---

### Post by Peachpit on 2008-05-10
Connected for the first time with wireless card but the browser
will not work after a re-boot.

  It just became obvious the only driver that will show as connected
for my card is wmp11v27 which is what it works on under XP on
the same computer. It even showed as connected with that driver under the ndiswrapper commands.

  Therefore, this had to be a configuration problem.  I was finally  able to configure manually, fire up Firefox and browse anywhere I want.

  But after a reboot, although I still show connected as a manual
config, Firefox will not work, get "address not found" for all pages.
I've gone into Firefox and tinkered with the proxy connections to
no avail.

  At one point I had the wireless bars showing, was apparently connected but Firefox would not work.

  But I can reboot, configure manually again and, bingo, Firefox works.
Until the next reboot that is. Starting to wonder why I'm doing this since 7.10 works so well. (Because I don't like giving up, that's why)

---

### Post by kevdog on 2008-05-10
For the times its not working you need to post some output rather than telling me its simply not working:

iwlist scan
ifconfig
ping google.com
route -n

They should help.

---

### Post by Ayuthia on 2008-05-10
You might want to make sure that you do sudo ndiswrapper -m, see that ndiswrapper is added to /etc/modules, and check the Making it Permanent section in the link provided in kevdog's post (#7).

---

### Post by Peachpit on 2008-05-10
One more thing.
When it shuts down now I get the message "unregister_netdevice: waiting for wlan1 to become free" ad infinitum. I have to turn off the computer before I can reboot.

---

