---
title: "New user needs help with wireless"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by JayP82 on 2010-03-18
Hi all

I have had a look in the netowrking and wireless threads but cannot find a solution for my problem so here it is.......

I am a new user (just installed today) and I cannot get connected to my wireless. It is being picked up by the machine but when it asks for my WPA I enter it, PC tries to connect and then asks for the WPA again and again and again.

Any help would be greatly appreciated.

Thanks

Jay

---

### Post by LowSky on 2010-03-18
turn the power off to the router and then plug it back in... now try connecting the computer. That sometimes works for me.

---

### Post by JayP82 on 2010-03-18
I'll give it a go.

Thanks

---

### Post by walt.smith1960 on 2010-03-18
> **LowSky said:**
> turn the power off to the router and then plug it back in... now try connecting the computer. That sometimes works for me.

If that doesn't work, try rebooting.  I sometimes get the "enter key" prompt repeatedly after several suspend-unsuspend cycles. A restart has always fixed it. The newer kernels in Karmic seem better; I haven't had to reboot in a couple months.

---

### Post by JayP82 on 2010-03-19
> **walt.smith1960 said:**
> If that doesn't work, try rebooting. I sometimes get the "enter key" prompt repeatedly after several suspend-unsuspend cycles. A restart has always fixed it. The newer kernels in Karmic seem better; I haven't had to reboot in a couple months.
 
 
This hasn't worked either, thatnks for the suggestion though. I'm so frustrated because it's probably something really simple but being new to Linux I don't know what it is. Anymore suggestions will be greatly appreciated.

---

### Post by zkriesse on 2010-03-19
Hi! First let me say welcome to the Linux OS and to the Ubuntu Forums! Ok.....wireless, let me think here....when it asks you for your WPA, you enter it but it doesn't connect? Or does it connect but keeps asking you for your password....little confused as to your question...

---

### Post by 2hot6ft2 on 2010-03-19
What version of ubuntu are you running?
And open a terminal
Applications > Accessories > Terminal
and run
```
lspci
```
That's LSPCI in lower case, then
```
lsusb
```
That's LSUSB in lower case, and post the results.
So we can see what wifi adapter you have.

Did you use the network manager applet in the top right panel to set your wireless connection up?

Right click on the applet and select Edit Connections
Then the wireless tab
Then select your connection and click on Edit
After putting in your password
Click the wireless security tab, select your security type and put your key in the box and click Apply.

Once it connects (if it does) click Close.

---

