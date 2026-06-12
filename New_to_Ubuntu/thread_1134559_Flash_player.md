---
title: "Flash player"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by truthbrush on 2009-04-23
Apologies, I feel a bit dumb asking this question. Does anyone know which version of flash to download?  Website tells me I need it and on the adobe site I have 4 choices.....

YUM
tar.gz
.rpm
.deb for Ubuntu 8.04

am guessing that the software is the same and these are  file formats.  Once downloaded do I just doule click to execute the installation.

Any help appreciated.

---

### Post by Claus7 on 2009-04-23
Hello,

what it interests you is the deb file and the tar.gz file.

Having gutsy gibbon the deb file might not work to you (double click it after having downloaded the file). 

Now the tar.gz file might work, depending on which version of browsers you have and which version of os you have (here gutsy). If you unzip it and make the installation manually (via command line) and it does not work, then you might need the previous version of flash, which searching a little you can find from the adobe site as well.

Try the deb first and see what it will happen. The other two ones are mostly for other distributions of linux.

Regards!

---

### Post by inobe on 2009-04-23
hi you can install from terminal rather quickly

```
sudo apt-get install flashplugin-nonfree
```

before you do that' do you need other like java and various codecs ?

if so you may as well go all out and do it all !

```
sudo apt-get install ubuntu-restricted-extras
```

or search in synaptic for them

flashplugin-nonfree

or 

ubuntu-restricted-extras

---

### Post by Claus7 on 2009-04-23
Hello,

> **inobe said:**
> hi you can install from terminal rather quickly

I hope that he will be able to do it. Because gutsy is a little bit old, with the command you provide I do not know which version of flash will be installed. By default I think that version 7 is installed, which in most web sites nowadays is not enough to display flash content. Of course it is easy enough to try and find out.

Regards!

---

### Post by inobe on 2009-04-23
i haven't used gutsy for more than a year.

so that you know' either from the adobe site or package manager you "will" get the very latest flash plugin.

package management will give you the plugin needed for your distro

---

### Post by Claus7 on 2009-04-23
Hello,

hope then that it will work with the versions of browsers that he has. Back in dapper, for example, flash 10 was not working with firefox 1.5 if I remember correctly. Gutsy will have a newer version of firefox (I do not remember which one).

Regards!

---

### Post by inobe on 2009-04-23
it makes complete sense to be cautious.


hey fella's if it starts to get bad' i suggest moving closer to 8.10 intrepid.

goodluck

---

### Post by truthbrush on 2009-04-25
Hi Guys,

Thanks for your posts.....I fell asleep at the keyboard and haven't been back on since.  Should have said that I have just ug'd to Jakalope the ref to 8.04 was just from the adobe download site.  I will try the install from terminal.

Thankyou for your advice and replies I always find these forums helpful and supportive, maybe one day I'll know enough about something to help other beginners out.

Cheers....

---

### Post by gandaran on 2009-04-25
> **truthbrush said:**
> Hi Guys,

Thanks for your posts.....I fell asleep at the keyboard and haven't been back on since.  Should have said that I have just ug'd to Jakalope the ref to 8.04 was just from the adobe download site.  I will try the install from terminal.

Thankyou for your advice and replies I always find these forums helpful and supportive, maybe one day I'll know enough about something to help other beginners out.

Cheers....
if you are on jaunty now the code for installing adobe flash from the repository is
```
sudo apt-get install flashplugin-installer
```

---

### Post by truthbrush on 2009-04-25
Have looked into these packages and have them installed, there was no change and couldn't view flash content on websites......read some more and found out that it could be a firefox issue and so have installed pakages

libswfdec-0.8-0
swfdec-mozilla

Now I have a player that launches, but it is unable to play the content when activated.  I will carry on reading.....any comments welcome.

---

### Post by gandaran on 2009-04-25
> **truthbrush said:**
> Have looked into these packages and have them installed, there was no change and couldn't view flash content on websites......read some more and found out that it could be a firefox issue and so have installed pakages

libswfdec-0.8-0
swfdec-mozilla

Now I have a player that launches, but it is unable to play the content when activated.  I will carry on reading.....any comments welcome.
if you have these packages installed they wont let firefox use adobe flash, it's very simple, for perfect working flash install only adobe flash!

---

### Post by truthbrush on 2009-04-25
Thanks, only running the flash package.....all good now.

Thanks

---

