---
title: "No networks or wifi turn on"
date: 2014-10-26
forum: Networking &amp; Wireless
---

### Post by quinton2 on 2014-10-26
I may not have worded the title very well but i have my system in dual boot it is an inspiron 1525. When i log into my ubuntu account and goto look to see if i have internet connectivity and i dont no networks show up or show a sign to turn on. the n program 
thing everyone told me to try and it doesnt work  what is the solution to this here problem

---

### Post by Bucky Ball on 2014-10-26
*Thread moved to **Networking & Wireless**.*

Welcome. What release of Ubuntu are you using?
Have you done an update with an ethernet cable and checked 'Additional Drivers'?

> the n program thing everyone told me to try and it doesnt work ... 


Have no idea what you're referring to, here. If it is ndiswrapper, DON'T install or use it! Avoid at all costs. You could make things much worse and more confusing. Ndiswrapper is largely superceded and sounds like you have been looking at old advice. It is rarely used and only on a few cards now.

If you want support, you need to try and be specific and give exact details and as much info as possible about what you've tried and where you're at (see the third link in my signature). Remember, we are not psychic, so help us to help you. ;)

Open a terminal and paste this in:

```
sudo lshw -C network
```

Hit return and paste the output back here, please (between [code] tags, see the last link in my signature).

---

### Post by wildmanne39 on 2014-10-26
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz)depending on the size of the file and it will be placed in your home folder. The wireless information will help to diagnose your wireless issue, the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the (wireless-info.txt, or wireless-info.txt.tar.gz) file as a zip file. 

If you do not have ethernet connection then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385).
Thanks

---

### Post by quinton2 on 2014-10-27
I have not tried to connect a wire from the router to my computer  i will try that ill come back with a response later today

---

### Post by Bucky Ball on 2014-10-27
Plug in a cable, get online, do an update, check 'Additional Drivers'. If nothing that brings no joy follow Wild Man's post.

---

