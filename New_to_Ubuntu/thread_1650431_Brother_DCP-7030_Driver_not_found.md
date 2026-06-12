---
title: "Brother DCP-7030 Driver not found"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by lorantjakab on 2010-12-21
Im trying to install the bro-dcp7030 printer driver but its not in ubi's menu. How can i install the right driver? Thank you

---

### Post by davidmohammed on 2010-12-21
drivers to download from [here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-7030") - instructions are just below the deb files you need to download.

---

### Post by lorantjakab on 2010-12-21
which one of the following do i use for linux/ubuntu? lpr or cupswrapper-rpm or deb?:KS

---

### Post by lorantjakab on 2010-12-21
why is it so hard to install a printer driver, its giving me a headache with all the binary code and stuff. can someone please tell me how install my printer driver painlessly?
thanks
 
eating advil for lunch:popcorn:

---

### Post by davidmohammed on 2010-12-21
umm - the instructions look very straightforward I think - you download the two deb files they suggest - lpr and cups wrapper.

Then you install the deb files

sudo dpkg <stuff> as per the examples in the documentation.

---

### Post by lorantjakab on 2010-12-23
Maybe im super stupid..... but i still cant get the printer working. I am having real issues with the coding.
I open terminal.
I have the 2 files saved in downloads, and i see them in the download window. Cups and deb files both there.
What exactly do i type into the terminal because nothing seems to work.
I have tried 2 days in a row, and its not working.
I have a dual setup. 
Can someone please show the code for me?
Windows is easier but i love ubuntu!


this is what is in my terminal: hi@hi-G41M-ES2H:~$

where do i go from hier? 

Thank you

---

### Post by davidmohammed on 2010-12-23
if you have saved them in your Downloads folder then open a terminal session and type

cd Downloads

the folder name is case-sensitive - so make sure you have a "capital" D rather than lower-case "d" for Downloads.

check you can see the files in that folder by typing

ls

then type the example code

e.g.

sudo dpkg -i <filename>

---

