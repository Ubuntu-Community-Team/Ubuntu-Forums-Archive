---
title: "Regression ..."
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2008-03-20
Broadcom 802.11 b/g WLAN: driver in windows is BCMWL6.SYS

Hi all. A final plea before I accept this situation once and for all.

Over christmas I set up both my laptop and desktop to dual boot Ubuntu Studio and a windows flavour. And both are performing beautifully to that end. Mission accomplished. It took hours days weeks and consumed a lot of my holiday, but I learnt a heap and eventually got there.

Except for wireless networking on the laptop. It took hours days weeks and ... I got nowhere and had to stop when study and uni called. So I am back to uni and ... back to Windows. :( 
Without the wireless, Linux laptop is useless for my study requirements (ad hoc network at uni and eth cables trailing through the house to my studio).

I have tried ndiswrapper and fwcutter, neither of which apparently can handle my Broadcom driver (bcmwl6). One thing I have noted is that Windows uses the BCMWL6.SYS file when I checked it out in device manager, not the BCMWL6.INF file which people seem to mention.

That I will try with Linux, but how and using what software or nifty technique?

Really am begging for someone to give me a step by step. I have researched this forever and spent days on it but no more spare time . Is there anyone out there using BCMWL6.SYS successfully with this card or any other workarounds that people have come up with?

Here's hoping 'cos I've really had it with the other OS ... after using Ubuntu, why would anyone want to go back to the needle in a haystack confusion and unreliability? I ask you???

Help, please. Currently drowning with not much time to spare ... I may have done all the right things but not maybe at the right times (as in the same time) or order.

---

### Post by Bucky Ball on 2008-03-20
Slight omission from last post ...

HP Pavillion dv6000 (dv6305us);
Broadcom 802.11 b/g WLAN

Incidentally, wireless was working very poorly when I installed Ubuntu and didn't have much of an idea. I thought I'd replace the driver with the windows one wrapped with ndiswrapper and that is when the quicksand appeared ...

---

### Post by zxscooby on 2008-03-20
What is the chipset of the card?

---

### Post by Bucky Ball on 2008-03-20
Hi there.

According to this website under the heading 'Broadcom 802.11 b/g WLAN'; 

[http://h20331.www2.hp.com/Hpsub/cache/295457-0-0-225-121.html](http://h20331.www2.hp.com/Hpsub/cache/295457-0-0-225-121.html)

... it is Broadcom 4306/2050 chipset

---

### Post by Bucky Ball on 2008-03-20
That card is the last on the list ...

---

### Post by deltaprime on 2008-03-20
how old is your laptop?
i got mine around that time from hp and mines an ipw3945
Intel pro wireless 3945 abg (the way its named in your list..)
here are some tips:

- make sure the switch is on
- use wireless assistant that you can install from synaptics manager
- try to unistall your card if it is intel and reinstall it :

type :

sudo modprobe -r ipw3945
sudo modprobe ipw3945

- if it is not intel just replace the "ipw3945" with the actual name of your driver

---

### Post by zxscooby on 2008-03-20
try reading this post
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/ndiswrapper-broadcom-bcmwl6-534767/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/ndiswrapper-broadcom-bcmwl6-534767/)

---

### Post by Bucky Ball on 2008-03-20
"What can I do now?
Please help me!"

... is the last post in that thread. The description sounds like a re-run of what I have been through, but with one or two extra dead ends. ;(

Might give it one more go over the weekend and see if I can't crack it this time.

---

### Post by Bucky Ball on 2008-03-20
BTW, Broadcom 802.11 b/g WLAN, as previously stated. Not intel.

---

### Post by zxscooby on 2008-03-20
Sorry, 
I was referring to the post that instructed the user to download the windows xp drivers
from the ndiswrapper wiki , as the vista drivers do not appear to work properly.
That seemed to solve the issue for that user but he developed problems latter from anouther action.

---

### Post by deltaprime on 2008-03-20
> **Bucky Ball said:**
> BTW, Broadcom 802.11 b/g WLAN, as previously stated. Not intel.



ok well thanks for rechecking that 
do you know the name of the drivers ???
did you try to reload them with modprobe
ARE they installed????

cant wait to get you working ;)

---

### Post by zxscooby on 2008-03-20
please post the output of 
```
lspci | grep Broadcom
```

---

### Post by Bucky Ball on 2008-03-20
Yep, bcmwl5 or spxxxx? Ndiswrapper tells me neither are compatible. I have had a little time away from the problem so give it a couple of hours later. Keep you posted and thanks. ;)

---

