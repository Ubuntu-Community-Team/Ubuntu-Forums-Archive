---
title: "Speedtouch Modem wont work"
date: 2005-06-11
forum: Networking &amp; Wireless
---

### Post by Dave_is_sexy on 2005-06-11
I followed the intructions on the wiki page and nothing happened. THe only change is that Ubuntu now takes slightly longer to start because it's loading the hotplug module.

I followed the instructions perfictly but they aren't complete. Once you've put the files in the right places and edited them propperly, you have to set things up in control panel > networking. I know my dial numbers are 0,38 for a BT line. 

I think it might be the modem path that's wrong on the second tabe. Does anyone know what this should be?

This is the fourth distribution I have tried to get the modem working on this year, and this time i am not giving up ^_^

---

### Post by desdinova on 2005-06-11
[QUOTE=Dave_is_sexy]I followed the intructions on the wiki page and nothing happened. THe only change is that Ubuntu now takes slightly longer to start because it's loading the hotplug module.

I followed the instructions perfictly but they aren't complete. Once you've put the files in the right places and edited them propperly, you have to set things up in control panel > networking. I know my dial numbers are 0,38 for a BT line. 

I think it might be the modem path that's wrong on the second tabe. Does anyone know what this should be?

This is the fourth distribution I have tried to get the modem working on this year, and this time i am not giving up ^_^[/QUOTE]
 I used the script and help at [http://speedtouchconf.sourceforge.net](http://speedtouchconf.sourceforge.net) to get mine working like a charm - had to do some tinkering with /etc/speedtouch.conf to get it working after a reboot - if you try it and it works, I can paste up my /etc/speedtouch.conf

---

### Post by Dave_is_sexy on 2005-06-11
Hey. 

Thanks that's cool, but with not knowing much linux yet i'd expect it to become ridiculously broken if i tried two install methods for the same thing. I'm sure I will be breaking the OS loads before I get something usable, but i've had so much stress just getting as far as i have, i'd like to stick with this direction.

---

### Post by desdinova on 2005-06-11
[QUOTE=Dave_is_sexy]Hey. 

Thanks that's cool, but with not knowing much linux yet i'd expect it to become ridiculously broken if i tried two install methods for the same thing. I'm sure I will be breaking the OS loads before I get something usable, but i've had so much stress just getting as far as i have, i'd like to stick with this direction.[/QUOTE]
 I tried that direction then this - its really a nobrainer... The webpage talks you completely through it

---

### Post by Dave_is_sexy on 2005-06-11
so i put sppedtouch.sh next to the firmware, run t and that's it? Why the hell isn't that in the wiki?

But the issue remains that the instructions are incomplete. Where do you put your username / password? What do you enter in the "route to modem" box? I'm sure that's all that's wrong with mine.

Could you look to see what's entered in yours please?
Thanks
Dave

---

### Post by desdinova on 2005-06-11
[QUOTE=Dave_is_sexy]so i put sppedtouch.sh next to the firmware, run t and that's it? Why the hell isn't that in the wiki?

But the issue remains that the instructions are incomplete. Where do you put your username / password? What do you enter in the "route to modem" box? I'm sure that's all that's wrong with mine.

Could you look to see what's entered in yours please?
Thanks
Dave[/QUOTE]
 The script I used for the webpage asks you all that interactively and configures everything...

---

### Post by Dave_is_sexy on 2005-06-11
Raises an eyebrow. Interesting. Guess it couldn't hurt i can always wipe the drive again. Off I go :)

---

### Post by desdinova on 2005-06-11
[QUOTE=Dave_is_sexy]Raises an eyebrow. Interesting. Guess it couldn't hurt i can always wipe the drive again. Off I go :)[/QUOTE]
 At the bottom of the page it says about some edits to a file called speedtouch.conf to get it to work at each reboot - heres mine

# SpeedTouch Config File
# Created by speedtouchconf.sf.net version 10.11.2004
# The speedtouch rc script assumes /usr/local/sbin is in the path...
# It does a . /etc/speedtouch.conf, so we can just add it to the PATH here.
PATH=/usr/local/sbin:$PATH
# LOAD_ directives should be 1 for modules, 0 if built into the kernel
LOAD_USBCORE=0
LOAD_USBINTERFACE=0
LOAD_NHDLC=1
# USB Interface - UHCI or OHCI
DEFAULT_USBINTERFACE="uhci_hcd"
# Path to microcode (eg. mgmt.o or alcudsl.sys from the official Alcatel drivers)
MICROCODE="/etc/ppp/microcode.dat"
# modem_run verbosity
VERBOSE=0
# Set this to 1 if you have configured the script
CONFIGURED=1



You may have to change 
DEFAULT_USBINTERFACE="uhci_hcd"

to one or other of the options

---

### Post by Dave_is_sexy on 2005-06-11
Think you've lost me there. I don't know how to find out the name of any usb socket. We seem to be adding extra steps. I am only 1 step away from finishing on the wiki method (the step that no-one wote yet)

The bloody installer is RPM based. it needs to be opened by Alien. It was obviouly too hard to write an auto-launcher into the script

---

### Post by desdinova on 2005-06-11
[QUOTE=Dave_is_sexy]Think you've lost me there. I don't know how to find out the name of any usb socket. We seem to be adding extra steps. I am only 1 step away from finishing on the wiki method (the step that no-one wote yet)

The bloody installer is RPM based. it needs to be opened by Alien. It was obviouly too hard to write an auto-launcher into the script[/QUOTE]

Which installer? The one on speedtouchconf is a .tar.gz?

---

### Post by Dave_is_sexy on 2005-06-11
The .sh file that is generated

---

### Post by Dave_is_sexy on 2005-06-11
IT says it is RPM based and that deb-something or other can't handle it.

---

### Post by desdinova on 2005-06-11
[QUOTE=Dave_is_sexy]IT says it is RPM based and that deb-something or other can't handle it.[/QUOTE]
 [http://sourceforge.net/project/showfiles.php?group_id=68502](http://sourceforge.net/project/showfiles.php?group_id=68502) is the link to the one I mentioned 

[http://prdownloads.sourceforge.net/speedtouchconf/speedtouchconf-2.0-beta2_16-May-2005.tar.gz?download](http://prdownloads.sourceforge.net/speedtouchconf/speedtouchconf-2.0-beta2_16-May-2005.tar.gz?download) is the actual link

---

### Post by Dave_is_sexy on 2005-06-11
I don't know how to use tarballs

---

### Post by desdinova on 2005-06-11
[QUOTE=Dave_is_sexy]I don't know how to use tarballs[/QUOTE]
 It comes with full instructions on the front page, and I quote:

> The documentation is available at SpeedTouch.SourceForge.Net but this script just does that lot for you, so you shouldn't need to bother reading documentation or understand anything about USB, PPP, or ADSL.

To use this script, you need to:

   1. Save the latest version of speedtouchconf.tar.gz, the script for configuring it all. The latest version is the first one listed on the page.
      This includes the speedtouch.sourceforge.net software.
   2. Extract the files: tar xzvf speedtouchconf-dd-mm-yyyy.tar.gz
   3. Change into the speedtouchconf directory: cd speedtouchconf-dd-mm-yyyy
   4. Get the Microcode from Alcatel (now Thomson):
          * Visit The Alcatel Microcode Download Page
            (fill in your details, uncheck the "spam me" checkbox, click "Continue" and select the "Binary" download link)
          * Or copy the alcaudsl.sys file from your working Windows installation
          * Another firmware file is currently available from speedtouch.sourceforge.net which is apparently quite reliable, and doesn't require you to enter any personal details.
          * For the silver modem, this firmware should be used. (The legality of this download is uncertain; the link may be disabled at any time). The Silver modem is now believed to work reliably - feedback appreciated. Just put the .ZIP file into the same directory as the speedtouchconf.sh script. Do not unzip it.
   5. Save the microcode (either speedmgmt.tar.gz, mgmt.o, alcaudsl.sys, or the .zip file) into the speedtouchconf-dd-mm-yyyy/ directory.
   6. # ./speedtouchconf.sh
   7. This should run something like this example. 

---

### Post by Dave_is_sexy on 2005-06-11
That does'nt run at all. it just flashes. Dunno why - I don't know hardly anything about this OS yet. I have decided that nautilus is the most annoying program i've ever run tho, re-sizing the window to tiny every time i open a folder and totally forgetting how bg i've told it to be, and that there's a LOT of manual shell editing to do to get basic things like "extract here" into the right click menus. But i'll learn all that.

So.. that file doesn't run. The other one did but failed cos it's RPM based. There wont be a reason i'm just cursed

---

### Post by Dave_is_sexy on 2005-06-11
OK that ran.

Now i have all the files it's made all over the filesystem, all doing nothing, with god knows how much extra config to do. The network settings are still wrong, it can't do anything like that, and i'm way further behind than i was 2 hours ago.

Guess I'll wipe all that off in the morning. Thanks for trying to help, but you said it was just running a file. The manual method is eaiar and cleaner, and at least i know what was where with that.

Time to see if that undo script works without deleting the files i already made myself

---

