---
title: "Question on how to install Virtual Box in  (10.10)version"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by tellnolies on 2011-03-15
When I downloaded Virtual Box, it said I was missing some file so I wasn't able to complete the installation. Is there a site I need to go to for the code for the Terminal?
I have been trying to find it out on youtube but its in another language so I don't know what the commands are. I see the ones for Bata but I have a AMD 64 bit Gigabite motherboard with a Nvidia 8800 gtx graphic's card.  I am trying to get Netflix set up for my 4yr old so she can watch her shows ( she's been driving me crazy) LOL. 
I really appreciate the info and tips that every one is sharing. Thank's

---

### Post by Rubi1200 on 2011-03-16
Why don't you just install it from the Ubuntu Software Center? Much easier I would say.

---

### Post by seawolf167 on 2011-03-16
Using the Ubuntu Software Center simply search for Virtual Box

The terminal command you are looking for is

```
sudo apt-get install virtualbox
```

---

### Post by vivek.pandey on 2011-03-16
> **seawolf167 said:**
> Using the Ubuntu Software Center simply search for Virtual Box

The terminal command you are looking for is

```
sudo apt-get install virtualbox
```

i guess you need to provide version also . so just type virtualbox on your terminal if its not installed you will get the full name of the package  but i suggest try from software center first

---

### Post by josephmills on 2011-03-16
I dont know if you want to be able to hook up usb to it or not but I would download from here [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) 
and then open it with ubuntu software center (download file then right click on it "open with ubuntu software center ) hope that this helps

---

### Post by beew on 2011-03-16
> **josephmills said:**
> I dont know if you want to be able to hook up usb to it or not but I would download from here [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) 
and then open it with ubuntu software center (download file then right click on it "open with ubuntu software center ) hope that this helps

If you want usb support, you can install the non-free version using the package manager as well, just have to add VB's ppa.

Here is how to get vb 4 in 10.10 using a repository, the advantage of that over downloading from the site is that you get updates automatically.
[URL="http://www.webupd8.org/2010/12/install-virtualbox-40-stable-in-ubuntu.html"]
http://www.webupd8.org/2010/12/install-virtualbox-40-stable-in-ubuntu.html[/URL]

---

### Post by seawolf167 on 2011-03-16
> **neo_aryan said:**
> i guess you need to provide version also . so just type virtualbox on  your terminal if its not installed you will get the full name of the  package  but i suggest try from software center first

The current release should be under "virtualbox", if you want to install a previous version, simply use tab-completion to see all the versions, i.e.

```
sudo apt-get install virtualbox[TAB][TAB]
```

---

### Post by tellnolies on 2011-03-22
Thank you all very much.
I had to start over cause some of the files were conflicting with each other and then I was able to get it to work.

---

