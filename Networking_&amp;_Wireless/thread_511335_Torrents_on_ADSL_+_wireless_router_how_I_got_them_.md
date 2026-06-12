---
title: "Torrents on ADSL + wireless router: how I got them to work"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by Mr. Swiveller on 2007-07-27
This 'howto' tells you how I got torrents to work on my Acer 5020, which is connected to ADSL through an E-tech wireless router. I tried many configurations, involving a large number of bittorrent clients, various firewalls, and a number of router setups. This is the one that worked. Before I used this setup, I kept getting NAT errors; now I get downloads of up to 250 kB/s +.

NB:

* Many of these tips will not apply to those who are not behind a router;

* I don't take any responsibility for what might happen once you start moddifying your router, network, and/or firewall settings.


-------


1) Find your computer's MAC address and make sure it is allocated a FIXED IP address by your router (usually accessible at the following address, through your browser: [http://192.168.1.1/](http://192.168.1.1/)). 

Your router's setup programme should allow you to manually link a fixed IP address to your MAC address if necessary.

> Tip 1: for some good advice on finding an IP address that will work with your particular setup see [http://portforward.com](http://portforward.com), a site with many tutorials.

> Tip 2: if you wish to find out your current IP address, type 'ifconfig' in a terminal. Look at the device through which you are connected with the internet (in my case, eth0), and note down the numbers behind the words 'inet addr'. Since your router allocated you these numbers, it should be OK to use them as a fixed IP address. 


2) Use the router's configuration programme to forward address 6881 to your new, fixed IP address. You may have to reboot the router (and quite possibly your PC too) in order for the new settings to take effect.

> Note: many people now use ports other than 6881 for bittorrent applications. Unfortunately, I never got setups other than the one described here to work, so I'll just stick with the default for the time being.


3) Install the Firestarter firewall. It's in the Ubuntu repositories. Note that you should not use two software firewalls simultaneously!

> Note: this proved to be the crucial change to my setup - I just couldn't get Kubuntu to accept any of the ports I had forwarded from my router before I installed Firestarter and set it up to accept torrents. 


4) After configuration (make sure that you read the instructions carefully), open up the 'policy tab' and right click on 'Allow Service'. Click 'add rule' and then pick BitTorrent from the drop-down menu. You shouldn't have to change the defaults, just click 'add'. Back in the main firestarter menu, click 'apply policy'.


5) Install the latest version of Wine. See [www.winehq.org](www.winehq.org) for instructions on adding the right repository if you would like to use Adept or a similar application (rather than compiling Wine yourself).


6) Download and install the Windows bittorrent client µTorrent from [www.utorrent.com](www.utorrent.com).

> Tip: the utorrent installer should launch automatically if you click the file. By default, the programme is installed to /home/[username]/.wine/drive_c/Program Files/uTorrent. If the installer fails to launch, try putting it on your desktop, and consequently invoking it by opening a terminal in your desktop folder and then running the command 'wine utorrent.exe'.

7) Run utorrent and make sure that it uses port 6881 for incoming connections. No other ports need to be configured.

If firestarter is running, everything should now work. You can invoke utorrent by using the 'wine' command in a terminal (syntax: wine [path]), or simply add utorrent to your K/Gnome menu. 

> Tip: in order to add uTorrent to your KMenu, right click on the K-menu, and click on 'edit item'. The editor opens; use it to add a new menu entry, and put the following in the white space after 'command': env WINEPREFIX="[FULL path to uTorrent.exe]". Do not forget to leave out the square brackets! ;-)


Cheers,

Swiveller

---

### Post by finalcut on 2007-07-30
thanx man, i took the easy way out and made an intern figure it out

---

### Post by ugm6hr on 2007-07-31
The other option is to just install KTorrent instead of WINE/utorrent, and load the UPnP plugin - which will automate the whole port forwarding issue for you.  No need to set ports on either your router or on Firestarter.

Much easier.

---

### Post by perdubug on 2007-12-22
My DELL n1100(Ubuntu 7.10) connected to ADSL through a D-Link wireless router. As ugm6hr mentioned above, KTorrent can work well without any additional configuration.

---

### Post by FoxOne on 2007-12-29
> **perdubug said:**
> My DELL n1100(Ubuntu 7.10) connected to ADSL through a D-Link wireless router. As ugm6hr mentioned above, KTorrent can work well without any additional configuration.

Same results, I used Ktorrent and my files get sucked down faster then... well they get sucked down pretty fast.

---

