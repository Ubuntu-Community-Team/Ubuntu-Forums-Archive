---
title: "The elusive all-ubuntu network how-to"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by uncleclinto on 2007-10-14
Okay, so everyone and their brother has a nifty how-to or tutorial on how to print to a Windows computer from Ubuntu, but where's the guide for those of us who have made the leap?  I have a printer in the living room attached to my wife's laptop (dapper) and I want to be able to print to it via an all Ubuntu LAN (Comcast & Linksys Router) from my Ubuntu Studio Desktop in the office.  This was no problem when my wife's computer was win2k, but I got sick of all the instability issues.  

Current Situation:
[LIST]
[*]I can share files
[*]All computers are connected to the internet
[*]I'm running DHCP (and have no idea how to assign a static ip to a particular box)
[/LIST] 

ps: I'm a big fan of step-by-step tutorials and even screenshots.  If anyone has one you could point me to, that would be swell. I can even work some CLi voodoo if it's spelled out for dummies. I'm not, on the other hand, a big fan of answers like, "just assign the lappy a static ip and add the appropriate numbers to you cupsd configuration file."

---

### Post by uncleclinto on 2007-10-15
Isn't there even some well-written documentation on this issue???  Anyone????????

---

### Post by uncleclinto on 2007-10-15
Okay, I found this, which looks promising...
[http://occy.net/printing](http://occy.net/printing)

...and I imagine there's some network-specific numbers I need to put in there.  Perhaps they're on this list (see attached screenshot of my router).  

If anyone cares to make this more than a one-man conversation and renew my confidence in these forums, feel free.

---

### Post by volkswagner on 2007-10-15
how did you print when connected to a win2k?

Did you use CUPs?

I like it for network printing.  Use the web interface.

---

### Post by dmizer on 2007-10-15
> **volkswagner said:**
> how did you print when connected to a win2k?

Did you use CUPs?

I like it for network printing.  Use the web interface.

that's what i was about to suggest.

browse to your server like so:
[INDENT][http://yourprintserverip:631](http://yourprintserverip:631)[/INDENT]

you'll have to add your server's login id to the cups group, but other than that ... ubuntu's already set up for printer sharing.  no need to install anything additional.

edit:
even better, cups can share printers to both linux and windows clients without configuring samba.

---

### Post by tact on 2007-10-15
> **uncleclinto said:**
> Okay, I found this, which looks promising...
[http://occy.net/printing](http://occy.net/printing)

...and I imagine there's some network-specific numbers I need to put in there.  Perhaps they're on this list (see attached screenshot of my router).  

If anyone cares to make this more than a one-man conversation and renew my confidence in these forums, feel free.

Hey there...  I haven't had the pleasure of an "all ubuntu" LAN at home or office and never tried to set up printer sharing from ubuntu to ubuntu.   thats the caveat.  :)

The information in the occy site seems pretty straightforward and clear.  Are you finding that so?

I know that you would need to plug in some numbers, and that is your question above so i will try to address that rather than the info in the site from occy.

First thing...  edit your last post and delete the image.   It shows your external internet IP address and thats an open invitation for hacker attack.  Quick!  ;)

Next....

---

### Post by tact on 2007-10-15
Next...

I did a quick google on your model of linksys device.  Looking for documentation to guide you through the process of having your DHCP server (inside the linksys router) assign reserved IP addresses to your computers.  Unfortunately the PDF on the site was "not found" so you are going to have to work through that a little unguided now (see below).

Before I start - Quickie comment/advice for a rainy day:
I note your linksys device does not have a dedicated printer port.  If the day comes you replace it look for one with a dedicated print server on it.   Then you can plug your home printer into the linksys (or its replacement) device and any machine on your LAN can print to it - no need to have a computer booted just so other machines can print to the printer.

Ok.  To work - the advice in occy's post/site seem to need you to put in IP addresses.  For that to work you need your machine with the printer attached to always have the same IP address.

There are a number of ways to do this I guess.  I would advise:
Let your linksys device continue to be a DHCP server but go through its setup and have it reserve specific IP addresses for the PC thats got the printer attached (and perhaps your other machine too).

As noted above  - I couldnt get a user guide for your router so I cannot guide you thru the steps to do this.  Its done in the router setup not ubuntu.

You choose the IP addresses for your machines, note them and use these numbers in the cupsys configs.

Your linksys router may want to know the MAC address of your computer's network cards for the process of reserving a specific IP address for a specific machine.  You can find the MAC address for your ubuntu machines in 
system>pref>hardware information.

Each network adapter in each computer has its own MAC address.  So in hardware information look for the reference to the relevant network adapter...  see next post for a screenshot.

---

### Post by dmizer on 2007-10-15
use cups.

easy two step method: [click here](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu?highlight=%28server%29%7C%28cups%29#head-6a3af6eb770f1dbc388e0574599943e463608bed)

---

### Post by tact on 2007-10-15
> **dmizer said:**
> use cups.

easy two step method: [click here](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu?highlight=%28server%29%7C%28cups%29#head-6a3af6eb770f1dbc388e0574599943e463608bed)

Actually - what dmizer says seems all that I'd expect is needed.   You did try just configuring system>admin>printing to share printers on both machines already - right?   

Noting you use feisty and the guide opens with 
"Printer sharing in Ubuntu 7.04 Feisty is very simple. It no longer requires manual editing of config files. " - so all the advice in the page by occy may only be for older systems?

In any case - Even in the guide that dmizer links to you need to enter in IP address.   So following on from my previous post:
Tho there are other ways to skin this cat I suggested you set your router to reserve fixed IP addresses to your computers (at least the one with the printer attached).

In summary:
- To achieve this you need to go through your router setup.  Its not set up in ubuntu.
- You MAY need to know the MAC address of your PC (with printer attached at least) to set up a reserved IP address inside the router
- To find out your MAC address System>Pref>hardware info
- look for your LAN adapter

Here attached is the promised screenshot

---

### Post by uncleclinto on 2007-10-18
no.... not Feisty.... once again, the computer with the printer is dapper.  I've tried ye olde "Global Settings" trick, but there is no "Share Printers" option there under dapper.  I'd love to just put Feisty on this print maching and be done with it but it's a pentium3 lappy with a 20 gig HD (11 gig of which looks like swiss cheese).  I had to do crazy partitioning magic just to get something running on this so unfortunately, I'm stuck with what I've got.

Now, Let's talk dapper...  I went into the web-based cups thing, but it asks for a username and password, which apparently isn't the default root user combo... so what the heck is it???  ...cause this browser-based utility seems a lot more user friendly than my Linksys router config or that darn cupsd.conf file.

---

### Post by uncleclinto on 2007-10-18
Okay, apparently this convoluted mess is how I set my cups password, but I need it translated into English:

```
 How to set CUPS password?

To run the CUPS server

/etc/init.d/cups start

To access the CUPS configuration from browser

http://localhost:631

To set the password for CUPS admin works

lppasswd -g <group> -a <user>

lppasswd -g sys -a root 
```

I assume that some of that is CLi voodoo, but do I write exactly that???  Do I replace "<group>" and "<user>" with something??  no clue...

---

### Post by dmizer on 2007-10-19
all you need to worry about is the last two lines.

enter these commands in the terminal:
```
sudo lppasswd -g cups -a youruserid
sudo lppasswd -g sys -a root
sudo /etc/init.d/cupsys restart
```

be sure to replace "youruserid" with your actual ubuntu username.

---

### Post by uncleclinto on 2007-10-21
Okay,

I followed dmizer's advice and set the passwords.  I restarted cups then the whole system because it said the command was not found.  I went into the cups interface and still couldn't log in!!  I can't log in with any combination of username and the password I made (not "root" "myuserid" or "lpadmin").  What am I missing here???  What's more is, two days ago (before updates) I could browse all of my network folders and move files between. Now I can brows the files but can't move anything either direction!!!  This is getting really frustrating.  I really want to be free of MS, but I have the flu, a new baby sitting next to me crying, work to do for my teaching job, online professor work, and web design work to do.  Frankly, I'm getting ready to say "screw it" and go back to all Windows so I can get something freaking done!  ](*,)

---

### Post by dmizer on 2007-10-21
try this:

```
sudo adduser cupsys shadow
sudo adduser [COLOR="Red"]youruserid[/COLOR] lpadmin
sudo /etc/init.d/cupsys restart
```

(replace <youruserid> with your actual ubuntu userid)

nothing we did would have any effect on your file sharing ability.  have you recently installed a firewall management program like firestarter?  if so, that would cause your file transfer issue.

---

### Post by uncleclinto on 2007-10-21
I did replace youruserid with my actual user id (the name I use to log into the box right??).  I just didn't list it here for security reasons (I seem to have a tendency to list secure info here).  

Anyway, I don't think anything we did with printing affected my shares.  I'm not even trying to move files between those particular computer.  I think it was the actual update from ubuntu that screwed me there.  I can no longer move files from my ubustu box to my dapper lamp box.  I use that server to host files to grab from school and to host my web site.  Now I can't put files on it.  I didn't install any firewalls.  Oh well!  More pains to deal with tomorrow.  It sucks that all of this is connected but won't speak to each other.

---

### Post by dmizer on 2007-10-21
my post above contains different commands.  please try them and retry the web interface.

what kind of file share (ftp, samba, nfs, http ...) do you have set up with your dapper box?

---

### Post by uncleclinto on 2007-10-21
screenshot of my error message (never go it before)

---

### Post by uncleclinto on 2007-10-22
Okay, I followed the most recent instructions and managed to get a check beside "share published printers".  On my ubustu box, I went to system>Administration>Printing to add the printer, and it was already there!  So, ever the pessimist, I decided to send a test page.  I get this message under my print manager thingy "Ready: Network host '192.168.1.100' is busy; will retry in 30 seconds..."  That's been the state for about an hour.  I don't think it'll go through.  poopers!  I was so close.

---

### Post by uncleclinto on 2007-10-23
i was sharing with samba

---

