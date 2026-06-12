---
title: "NUC6CAYH WIreless 3168"
date: 2017-11-18
forum: Networking &amp; Wireless
---

### Post by bean1945 on 2017-11-18
Has anyone had any success accessing their wireless network with the Intel 3168 adapter (on the  above NUC or any other one)?

Jerry

---

### Post by wildmanne39 on 2017-11-18
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by bean1945 on 2017-11-18
The problem is that I cannot access the internet with the 3168. but must use an external usb adapter. I would assume that then the script would not be meaningful?

Jerry

---

### Post by wildmanne39 on 2017-11-18
Okay, it gives us the information needed to help you, I do not know why you would make such an assumption.

---

### Post by wildmanne39 on 2017-11-18
After you run it the first time and post the results, unplug your usb adapter and run it again using the following command:
```
./wireless-info
```
that will tell us the information just for you internal card.

---

### Post by bean1945 on 2017-11-18
wildmanne39

[I]s this what you need?

[http://paste.ubuntu.com/25992945/](http://paste.ubuntu.com/25992945/)

[/I]

---

### Post by wildmanne39 on 2017-11-18
Yes it is, will you also post the results without the usb adapter plugged in please?

---

### Post by bean1945 on 2017-11-18
When I ran the command w/o the usb, it produced a .gz file. How do I get that to you?

---

### Post by bean1945 on 2017-11-18
I put the output under "No usb" on pastbin. Will that work?

---

### Post by bean1945 on 2017-11-18
I now pasted the no usb output on ubuntu pastebin under Jerry. Hope that is what you need.

---

### Post by wildmanne39 on 2017-11-18
Please use the command I gave to run the script after you unplug your adapter, the command is in my third post I believe, you can do that because the script is already on your computer and will not require an internet connection and it will replace the file previously created, then just post that file to pastebin at the following link, then post the link here to the file on pastebin.

This way we can see the output with the adapter plugged in and without so we only see what is going on with the internal card.

[https://pastebin.com/](https://pastebin.com/)

---

### Post by bean1945 on 2017-11-20
Were you able to find the output without the USB adapter?

---

### Post by wildmanne39 on 2017-11-20
No, I do not see the whole output of the script for your internal card only, when you run it post it to a new pastebin link so we can see only that information, I do not want to see the usb adapter or the driver for it loaded in that output.

Thanks

---

