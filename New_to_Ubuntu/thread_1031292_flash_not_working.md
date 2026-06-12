---
title: "flash not working"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by x0prah_Winfr3yx on 2009-01-05
Hello all, thanks for taking time to read my thread.

my problem is that I cannot get flash to work in my firefox. i can't view youtube, myspace players, or anything that requires the plugin.

i have installed the latest drivers, so what else can i do to get things rolling?

thanks again.

---

### Post by RomeReactor on 2009-01-05
Hi. Close Firefox and try removing Gnash (in case it's installed) and make sure Flash is installed:
```
sudo aptitude purge gnash gnash-common mozilla-plugin-gnash && sudo aptitude install flashplugin-nonfree
```
Then open Firefox again and see if Flash is working now.

By the way, there are plenty of threads related to Flash already posted. Searching the forums before posting is a great resource.

---

### Post by x0prah_Winfr3yx on 2009-01-05
thanks for the reply.

though your suggestion didn't work for me, i guess i'll go back to crawling through previous threads.

---

### Post by RomeReactor on 2009-01-05
Which version of Ubuntu are you running? Do you get Flash listed by typing **about:config** in the address bar in Firefox?

---

### Post by x0prah_Winfr3yx on 2009-01-05
sorry for the response time, i was checking into other threads for a solution.

i'm running version 8.10

in the about:config, i only instance of the word flash i see is accessibilty.typeaheadfind.flashbar, but i know that's not it.

i'm downloading from adobe's downloads section, a .deb file. it says it's installed already.

---

### Post by pdtpatrick on 2009-01-05
run suda apt-cache search flash 

and you should see something like flashplugin-nonfree
..

close firefox and run

sudo apt-get update;sudo apt-get install flashplugin-nonfree

then reopen firefox and test it out. 

If that doesnt work then go to adobe.com and download the flash player (.deb version)

and to install it, switch to the location where you saved the file and run:

sudo dpkg -i xxxxx.deb

---

### Post by stchman on 2009-01-05
Go to Tool--->Add-ons and select the Plugins tab.  What version of Flash does it say you are running?

---

### Post by x0prah_Winfr3yx on 2009-01-05
it says i'm running Shockwave Flash 9.0 r999

when i run sudo apt-get install flashplugin-nonfree

i see:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by donkyhotay on 2009-01-05
Odd, that means it's already installed even though firefox doesn't recognize it. Try removing/adding it again with:
```
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

---

### Post by wolfen69 on 2009-01-05
let's start over. go to synaptic and completely remove flash. then open a terminal and: ```
sudo apt-get clean && sudo apt-get autoremove
``` then go [here]("http://get.adobe.com/flashplayer/") and download the .deb flash file for ubuntu. click to install. restart firefox if open.

---

### Post by x0prah_Winfr3yx on 2009-01-05
well i tried that to no avail.

it's weird alright, i can right click on where a flash video should be and i see the normal options, playing, enable audio, properties, blah blah.

but the actual player never shows up.:confused:

---

### Post by wolfen69 on 2009-01-05
check the last post (mine) on the previous page. we posted at the same time.

---

### Post by x0prah_Winfr3yx on 2009-01-05
> **wolfen69 said:**
> let's start over. go to synaptic and completely remove flash. then open a terminal and: ```
sudo apt-get clean && sudo apt-get autoremove
``` then go [here]("http://get.adobe.com/flashplayer/") and download the .deb flash file for ubuntu. click to install. restart firefox if open.

darn, that didn't do it for me either. wowsers.

---

### Post by x0prah_Winfr3yx on 2009-01-05
screenshot.

how ever will i survive without my youporn.com?!?

---

