---
title: "how to find hardware elements"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by Ewan Cameron on 2009-09-29
I am running ubuntu on my laptop  (Sony VAIO VGN-TZ37GN) and am  loving its cleanliness and speed, but have been unable to get it to recognize the built in web cam or the built in card reader.

I have done some searching on this but have had trouble understanding the pages I have found, as I am an absolute beginner with linux.

I would very much appreciate any pointers on how to progress this issue

cheers

KC

---

### Post by muteXe on 2009-09-29
not in front of my linux machine but 'lspci' and 'lsusb' might give you info about some of your hardware.

---

### Post by lisati on 2009-09-29
> **muteXe said:**
> not in front of my linux machine but 'lspci' and 'lsusb' might give you info about some of your hardware.

+1: The commands mentioned by mutexe are a good first port of call for learning what's "under the hood". Also of interest is "dmidecode", which provides a lot of potentially useful information. (You will need to run it with [root privileges]("https://help.ubuntu.com/community/RootSudo"))

edit: Thanks, ad_267, and well spotted!

---

### Post by ad_267 on 2009-09-29
Since this is your first post I'll just add that you can enter those commands by opening up a terminal from Applications - Accessories - Terminal and entering:
```
lspci
lsusb
```

To run dmidecode enter:
```
sudo dmidecode > ~/Desktop/dmidecodeinfo.txt
```

You will then have to enter your password and press enter (nothing will show up on the screen while you type your password). Then there will be a file on your desktop which you can attach to a post.

There is also a graphical interface (gnome-device-manager) for seeing information about what hardware you have.

---

### Post by farsight on 2009-09-29
Regarding webcam recognition; a guide I read not too long ago, whilst installing Ubuntu Netbook remix, informed me to activate the built in webcam through BIOS. Using an eee pc 1000 I had to hold F2 (I believe) to load the BIOS settings screen, navigate to a given page and change webcam from disabled to enable. I confirmed this worked using the program "Cheese."

I know we are using different laptops/netbooks, but both have built in webcams and so I reason this may prove to be a simple solution.

I hope this helps you,

Thanks,
Farsight

---

### Post by jward3010 on 2009-09-29
Yep "Cheese" will check if your webcam works.
Go to a terminal and type:
```
sudo apt-get install cheese
```

An easy to read version of your hardware:
```
sudo lshw -html > hardware.html
```
This will dump a html page in your home folder which you can open in firefox.

---

