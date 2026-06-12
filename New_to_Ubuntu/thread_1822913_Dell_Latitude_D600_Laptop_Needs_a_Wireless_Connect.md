---
title: "Dell Latitude D600 Laptop Needs a Wireless Connection"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by TAspr on 2011-08-11
Hi folks, can you please explain how to get the wireless on my Dell Latitude D600 to connect wirelessly?  No matter what I do I cannot get it to connect.

I am using 10.4 Ubuntu.

---

### Post by amjjawad on 2011-08-11
> **TAspr said:**
> Hi folks, can you please explain how to get the wireless on my Dell Latitude D600 to connect wirelessly?  No matter what I do I cannot get it to connect.

I am using 10.4 Ubuntu.

Are you able to connect via LAN? Wired Connection?

From Terminal, please post the output of:

```
sudo lshw -C network

```

and please wrap up the text with "CODE" tags or highlight the output and click "#".

---

### Post by TAspr on 2011-08-11
Yes I am, I cannot get it to work at all now... hold on..

Never mind, the Hard Drive is bad.

---

### Post by TAspr on 2011-08-14
Well, I was not sure how to encapsulate the output in code, but here goes:

---

### Post by TAspr on 2011-08-14
Anyone?

---

### Post by spcwingo on 2011-08-14
While plugged in via ethernet cable, run this command:

```
sudo apt-get install -y b43-fwcutter
```

---

### Post by TAspr on 2011-08-14
> **spcwingo said:**
> While plugged in via ethernet cable, run this command:

```
sudo apt-get install -y b43-fwcutter
```


Then what do you do?

---

### Post by spcwingo on 2011-08-14
If I'm not mistaken (it's been a while since I set one of those laptops up), just reboot and enjoy.  :)

---

### Post by waynefoutz on 2011-08-15
I have that laptop, just retired it in fact, I had better luck with the STA driver.

---

### Post by TAspr on 2011-08-15
Still cannot get this to work...  Even after the update.  Bummer.

---

### Post by waynefoutz on 2011-08-15
It should have a broadcom in it. Get it plugged into a router with an ethernet cable, open up a terminal, type ```
sudo apt-get update
``` Then open up "Additional drivers" Pick the STA driver if it's available, activate it, then reboot.

---

### Post by spcwingo on 2011-08-15
Try this in a terminal:

```
b43-fwcutter
```

Let me know if that does the job.  If not, please post the output of that command.

---

### Post by TAspr on 2011-08-15
Beautiful!  Got it to work like a charm.  After rebooting, it did not work, but after removing and adding the wireless connection, it did.  Awesome!  Thank you friends.

---

