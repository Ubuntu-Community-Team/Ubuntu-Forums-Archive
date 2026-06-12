---
title: "How do I install Flash Player 10 to Ubuntu 8.10?"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by racie on 2009-02-08
Sorry, I'm a newbie to Ubuntu and I can't watch Youtube videos and other things because I need the latest version of Adobe Flash.  Do I download the .tar.gz extension?  How do I install it?  Thanks.

--Racie

---

### Post by tehforum on 2009-02-08
Download the latest deb from [here.]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb")

Once downloaded, and on your desktop, just double click and follow the simple on-screen instructions.

---

### Post by racie on 2009-02-08
The .deb file does not work for me.  When I open it, there is red writing that says "Error: Wrong architecture 'i386'," and the intall button is grayed out.

---

### Post by tehforum on 2009-02-08
Woops, must be because it auto detected my settings.

Try downloading the deb from [this download page ]("http://get.adobe.com/flashplayer/?promoid=DXLUJ")

---

### Post by racie on 2009-02-08
That's where I got it from originally.  I downloaded it again and I get the same thing.  If it helps, I'm running Intrepid Ibex.

---

### Post by kestrel1 on 2009-02-08
I would say your best thing to do is do a search with Google for Flash Player & go to the Adobe site that comes up. It should detect your system & all you need do is select the deb package.

---

### Post by Firestem4 on 2009-02-08
oops misread

---

### Post by howefield on 2009-02-08
Try downloading it from here 

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)


Remember, this is not a finished release, but seems to work very well.

---

### Post by racie on 2009-02-08
> **kestrel1 said:**
> I would say your best thing to do is do a search with Google for Flash Player & go to the Adobe site that comes up. It should detect your system & all you need do is select the deb package.

The .deb file does not work for me.  Please read other posts before posting.

*edit* [quote=howefield]Try downloading it from here

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)


Remember, this is not a finished release, but seems to work very well.[/quote]

Does this mean I have the 64-bit version of Ubuntu?

---

### Post by kestrel1 on 2009-02-08
Have you tried the Google search?

---

### Post by racie on 2009-02-08
> **kestrel1 said:**
> Have you tried the Google search?

No, I haven't.  But I've already downloaded the .deb file from the **official** website and it doesn't work for me.  I came here to get help, not to have people telling be to search random things in Google.

---

### Post by Old *ix Geek on 2009-02-08
> **racie said:**
> The .deb file does not work for me.  When I open it, there is red writing that says "Error: Wrong architecture 'i386'," and the intall button is grayed out.How are you trying to install it?

---

### Post by RomeReactor on 2009-02-08
Hi. There's no .deb for the 64 bit version of Flash 10 yet. You can, however, install the 32 bit version from the repositories:
```
sudo aptitude install flashplugin-nonfree
```

---------------------------------------------------------------------------------

Or, if you *really* want the 64 bit version of Flash, make sure you have Ubuntu 64 bit. Run:
```
uname -m
```
If the result is **x86_64**, you have Ubuntu 64 bit. You can then install the 64 bit version of Flash using this script, which will download the package from [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz"). First, open Gedit:
```
gedit Flash64
```
Once Gedit opens, paste the following there:
```
#!/bin/bash
aptitude -y purge flashplugin-nonfree nspluginwrapper gnash mozilla-plugin-gnash gnash-common
updatedb
for x in `locate libflashplayer.so`; do rm $x; done
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
tar -xvzf libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
cp ~/libflashplayer.so /usr/lib/mozilla/plugins
rm ~/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
rm ~/libflashplayer.so
```
Save the file, close Gedit, and make the file executable:
```
chmod +x Flash64
```
and run the script:
```
sudo ./Flash64
```

---

### Post by kestrel1 on 2009-02-08
Hardly random.
You must have downloaded the wrong deb file.

---

### Post by racie on 2009-02-08
How do I tell if I have the 64-bit version of Ubuntu???

---

### Post by howefield on 2009-02-08
> **racie said:**
> Does this mean I have the 64-bit version of Ubuntu?

Well, you said the 386 was the wrong architecture..

Type in a terminal

```
uname -m
```

to find out what version you have.

---

### Post by Old *ix Geek on 2009-02-08
> **racie said:**
> How do I tell if I have the 64-bit version of Ubuntu???When you go to this page, [http://get.adobe.com/flashplayer](http://get.adobe.com/flashplayer) does it correctly identify your Linux version?

---

### Post by racie on 2009-02-08
When I typed ```
uname -m
``` I got:
```
x86_64
```

Why do I have the 64-bit version of Linux?  I installed it through Wubi on my Vista computer.

---

### Post by deepclutch on 2009-02-08
download the 64-bit plugin from labs.adobe.com for Linux(beta).
then ,copy the plugin to /usr/lib/firefox/plugins .

---

### Post by racie on 2009-02-08
> **RomeReactor said:**
> Hi. There's no .deb for the 64 bit version of Flash 10 yet. You can, however, install the 32 bit version from the repositories:
```
sudo aptitude install flashplugin-nonfree
```

---------------------------------------------------------------------------------

Or, if you *really* want the 64 bit version of Flash, make sure you have Ubuntu 64 bit. Run:
```
uname -m
```
If the result is **x86_64**, you have Ubuntu 64 bit. You can then install the 64 bit version of Flash using this script, which will download the package from [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz"). First, open Gedit:
```
gedit Flash64
```
Once Gedit opens, paste the following there:
```
#!/bin/bash
aptitude -y purge flashplugin-nonfree nspluginwrapper gnash mozilla-plugin-gnash gnash-common
updatedb
for x in `locate libflashplayer.so`; do rm $x; done
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
tar -xvzf libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
cp ~/libflashplayer.so /usr/lib/mozilla/plugins
rm ~/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
rm ~/libflashplayer.so
```
Save the file, close Gedit, and make the file executable:
```
chmod +x Flash64
```
and run the script:
```
sudo ./Flash64
```

It said that there were 0 files to install.  Youtube videos/games/etc. still say I need the latest version of Adobe Flash player.

---

### Post by RomeReactor on 2009-02-08
Did you restart Firefox? The changes won't take effect until you do so.

---

### Post by racie on 2009-02-08
Oh yeah.  It works now.  Thanks. :biggrin:

---

### Post by demarshall on 2009-02-10
I'm running 32 bit Kubuntu Intrepid and reinstalled Flash 10 but still cannot get videos to run either in YouTube or elsewhere. Any suggestions?

Can I uninstall it and reinstall it? How do I know what version Firefox is using?

---

### Post by kestrel1 on 2009-02-10
> **demarshall said:**
> I'm running 32 bit Kubuntu Intrepid and reinstalled Flash 10 but still cannot get videos to run either in YouTube or elsewhere. Any suggestions?

Can I uninstall it and reinstall it? How do I know what version Firefox is using?

You may be better off starting a new thread if you have tried what has been suggested in this thread. If you do, could you post back here with a link to your thread.

---

### Post by demarshall on 2009-02-10
Okay.

Here is the link to the new thread:
[http://ubuntuforums.org/showthread.php?p=6711963](http://ubuntuforums.org/showthread.php?p=6711963)

---

