---
title: "How do i get youtube to play"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by Leapin_Lee on 2009-05-17
Hi. I have just successfully installed the dual boot 9.04 . I have a gateway FX7811 laptop I'm running 64 bit version of Jaunty.I have installed Jaunty by reading for hours and hoping for the best. So far so good. Can someone please tell me exactly step by step what I need to do to get youtube to play? It says I need a flash player but the adobe it sent me too doesn't install.

---

### Post by vegetarianshrimp on 2009-05-17
1. Open the Terminal (Applications > Accessories > Terminal). 
2. Type in ```
sudo apt-get remove flashplugin-nonfree
``` and press enter
3. It might ask for your password, type it in. No as asterisks will show up, but it will still work. press enter after words.
4. Open Software Sources (System > Administration > Software Sources)
5. Click the check box next to the line > **[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty **partner 6. Click close, and if a window pops up, press reload.
7. Open the Terminal again (Applications > Accessories > Terminal) and type in ```
sudo apt-get install adobe-flashplugin
```
8. That's it, you're done!

---

### Post by zvacet on 2009-05-17
In applications>accessories>terminal type

```
sudo apt-get install ubuntu-restricted-extras
```

That will give you more then just flash.If you are not satisfied with flashplugin-nonfree then edit your source list 

```
gksudo gedit /etc/apt/sources.list
```

and add this line 

> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

Save and close file.

```
sudo apt-get update
```

Go to the synaptic and install **adobe-flashplugin** and remove flashplugin-nonfree.

---

### Post by Ms_Angel_D on 2009-05-17
You may want to have a look at this too: [http://www.psychocats.net/ubuntu/nonfree](http://www.psychocats.net/ubuntu/nonfree) & This too ;) [http://ubuntuforums.org/showthread.php?t=1151875](http://ubuntuforums.org/showthread.php?t=1151875)

---

### Post by bumanie on 2009-05-17
The only way I could get flash to work on 9.04 64bit was to follow [this]("http://www.google.com/cse?cx=partner-pub-2070091971271392%3Aougxymc6y19&ie=UTF-8&q=my+science+is+better+flash+64+bit&sa=Search"). Hope it helps. I tried a number of methods, but this is the only one that worked.

---

