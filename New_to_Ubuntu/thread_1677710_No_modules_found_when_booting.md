---
title: "No modules found when booting"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by bernard079 on 2011-01-29
i sucessfully install ubuntu on my netbook after several attemp 
but the problem now is every time i shutdown and restart my netbook am having problem... 
its say on the screen something like this 

"no module name found aborted 
operating system not found" 

then ill try to install again the ubuntu from usb drive then i can boot again to ubuntu or window 
then when i shutdown and restart my netbook same problem i incounter 
then i install again ubuntu just to go to window haaaah am tired of this.. i wish i did not install ubuntu..now i dont want to shutdown my netbook coz i think ill be having the same problem again and i dont to install again and again just to open the window. 
how can i remove ubuntu? 

can anyone help me am begging plsssss....?

---

### Post by Rubi1200 on 2011-01-29
> **bernard079 said:**
> i sucessfully install ubuntu on my netbook after several attemp 
but the problem now is every time i shutdown and restart my netbook am having problem... 
its say on the screen something like this 

"no module name found aborted 
operating system not found" 

then ill try to install again the ubuntu from usb drive then i can boot again to ubuntu or window 
then when i shutdown and restart my netbook same problem i incounter 
then i install again ubuntu just to go to window haaaah am tired of this.. i wish i did not install ubuntu..now i dont want to shutdown my netbook coz i think ill be having the same problem again and i dont to install again and again just to open the window. 
how can i remove ubuntu? 

can anyone help me am begging plsssss....?
Hi and welcome to the forums :-)

You really need to start your own thread to deal with this.

That said,
from the LiveUSB please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
 sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by CharlesA on 2011-01-29
bernard079, please don't hijack someone else's thread.

I've moved your post to it's own thread.

Start off with following Rubi's instruction and that'll give us a bit more info as to what is going on.

---

