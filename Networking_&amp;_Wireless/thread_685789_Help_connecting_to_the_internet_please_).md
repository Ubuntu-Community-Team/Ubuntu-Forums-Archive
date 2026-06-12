---
title: "Help connecting to the internet please :)"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by CloudFX on 2008-02-02
Hi Ubuntu Forums!,

I recently installed Ubuntu on to my computer (I'm dual booting, right now im on Vista). I'm unfortunately having troubles connecting my computer to my router wirelessly. The only way for a computer to access my router is if the MAC address of that computer is entered into it. Once this happens, the Wireless Network is then connectable to. No password is required. I tried entering the Network name using Manual Configuration, and the network icon in the top right turned to the 5 bars, but it had 0% connection. When I am in Roaming Mode, no wireless connections appear for me to connect to.

I also need to know if my MAC address is different on Ubuntu than it is on Vista, and also how i can access it via Terminal (like ipconfig in Command Prompt).

Any help would be greatly appreciated, thanks much!:)

---

### Post by shad0w_walker on 2008-02-02
Your MAC address is unique to the network card and won't change from OS to OS. I'm afraid I can't really provide any help on the problem but just as a heads up, MAC addresses are quite easily faked and sniffed to gain access to a wireless network.

---

### Post by hahahan on 2008-02-02
CloudFX,

As far as my experience goes the MAC of your wirelesscard is the same what ever you boot Vista or Ubuntu thus a MACfilter on the router should not be a problem.
To manualy set a mac of your card use ifconfig:

ifconfig ethx down
ifconfig ethx hw ether YOURMAC(XX:XX:XX:XX:XX:XX)
ifconfig ethx up

Hopes it helpes you, regards.

---

### Post by CloudFX on 2008-02-02
Thank you very much to both of you.

shad0w_walker;
Fortunately, the only person who has access to my router is my dad. Its password protected, and only he can access it from his computer.

Hahahan;
where the X's are, is that where I enter my current MAC address, or do I type in those X's? And sorry, what do you mean by 'To manually set a MAC'?

---

### Post by hahahan on 2008-02-02
Your MAC hassen't changed we think, it dosn't matter what OS you boot, it's in the hardware or firmware of the wirelesscard.
When you are shure the MAC is the problem here you can change it easily with ubuntu.
Wiith manualy I mean from terminal. "ifconfig" is just one of those wonderfull tools ubuntu is shipped with.

Regards

---

### Post by CloudFX on 2008-02-02
Ok, I understand it now. But I still need to know what and if to replace the X's with.

---

### Post by shad0w_walker on 2008-02-03
You need to replace the X's with your MAC address if I understand that post correctly.

---

### Post by wahr on 2008-02-03
I have the same router setup, and while I havent resolved the issue entirely, a big part was the requirement for the ESSID (the network name).  

I entered it and didn't have an issue after that.

---

