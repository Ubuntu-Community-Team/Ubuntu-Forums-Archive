---
title: "Issue connecting to home wi-fi with NETGEAR AC600 Dual Band"
date: 2017-01-01
forum: Networking &amp; Wireless
---

### Post by manatee.madness on 2017-01-01
At the moment I am stuck using the Ethernet cable downstairs to access the Internet, and I would like to move to my room upstairs. I have the NETGEAR AC600 Wireless AC Adapter which is supposed to be plug-in and use, but I don't see anything other than the wired connection. There was a thread about a fix from 2014 which I followed exactly and I didn't see anything that would show it worked. Running the CD to install doesn't work, as an error shows up (it just says an error occurred, nothing else). My dad and I cannot figure out WHY it isn't working, and neither of us really understand the code languages so I can't just screw around with the terminal to figure it out.

This is the first computer that I've used Linux on, and it's built from scratch. Anyone who can fully explain what I should do what what to look for to know if it worked would be of great help. And please, try and keep it simple as I'm not very technologically gifted.

---

### Post by wildmanne39 on 2017-01-01
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.

---

### Post by manatee.madness on 2017-01-01
Umm..... I ran your command and I lookeed at the .txt file but I have NO idead what any of it is supposed to mean. Do you want me to paste the file here? I'm also not really sure what "code tags" are.

---

### Post by wildmanne39 on 2017-01-01
Just paste the output here:
[http://pastebin.com/](http://pastebin.com/)
then paste the link back here.
Thanks

---

### Post by manatee.madness on 2017-01-02
Here's a link to the page. Hope it helps.

[http://pastebin.com/tKe30QGR](http://pastebin.com/tKe30QGR)

---

### Post by wildmanne39 on 2017-01-02
If you have a system with secure boot you will need to go into the bios and turn it off then do the following by coping and pasting the code one line at a time, To open the terminal CTRL+ALT+T:
```
wget http://mirrors.kernel.org/ubuntu/pool/universe/r/rtl8812au/rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu2_all.deb
sudo dpkg -i rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu2_all.deb
```
Reboot

---

### Post by manatee.madness on 2017-01-02
I HAVE WIFI! I deleted the PK key or whatever to disable secure boot, and I didn't even have to input your code, I was able to connect to the wifi anyway.

Should I still enter the command? What does it do?

Thank you very much for the help.

---

### Post by Hadaka on 2017-01-02
Hi, glad you found a solution.
The code Wildmanne39 suggested loads the rtl8812au module
for your Wireless card....to verify you have the correct module loaded
please copy and paste...then post the output of.,,
```
lspci -nnk | grep -iA2 net
```
it should read...Kernel driver in use: rtl8812au
*If it does you should be all set.And if you are satisfied with the result
please take the time to mark your thread SOLVED, by clicking THREAD TOOLS
near the upper right  and choose SOLVED.
thanks.

---

### Post by wildmanne39 on 2017-01-02
Glad it is working!
Enjoy!

---

