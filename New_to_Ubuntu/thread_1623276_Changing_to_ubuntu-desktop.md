---
title: "Changing to ubuntu-desktop"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by Avidanborisov on 2010-11-16
Hello,
Recently I created a live-usb with multibootiso including ubuntu netbook remix. I didn't like the ubuntu netbook remix even it is said it is just for small screens like my netbook. So, in terminal I wrote ```
sudo apt-get install ubuntu-desktop
```
and everything went fine and it installed ubuntu-desktop and I have the option to set Ubuntu-desktop in login settings. but, it seems that everytime I turnoff ubuntu it deletes all the recent data and never switches into ubuntu-desktop.
btw, The only thing I liked in Ubuntu netbook remix is the ubuntu button that was used to search apps. How can I get this button in ubuntu desktop too?

---

### Post by DarrenMR415 on 2010-11-16
I did this same thing, this is the code I used in the terminal.  Remembers the version I was using every time.

```
sudo aptitude install -y ubuntu-desktop ubuntu-netbook
```

---

### Post by philinux on 2010-11-16
> **Avidanborisov said:**
> Hello,
Recently I created a live-usb with multibootiso including ubuntu netbook remix. I didn't like the ubuntu netbook remix even it is said it is just for small screens like my netbook. So, in terminal I wrote ```
sudo apt-get install ubuntu-desktop
```
and everything went fine and it installed ubuntu-desktop and I have the option to set Ubuntu-desktop in login settings. but, it seems that everytime I turnoff ubuntu it deletes all the recent data and never switches into ubuntu-desktop.
btw, The only thing I liked in Ubuntu netbook remix is the ubuntu button that was used to search apps. How can I get this button in ubuntu desktop too?

When you created the live usb did you make it with persistence enabled?

---

### Post by Avidanborisov on 2010-11-16
> **DarrenMR415 said:**
> I did this same thing, this is the code I used in the terminal.  Remembers the version I was using every time.

```
sudo aptitude install -y ubuntu-desktop ubuntu-netbook
```

> **philinux said:**
> When you created the live usb did you make it with persistence enabled?
1. Thank you, I will try!
2. Well, I never saw the option to make it persistence enabled... Maybe it will work for desktop environment but what about programs and drivers? Every time I choose Ubuntu from GRUB4DOS I need to install additional drivers again. How can I make it persistence enabled now?

---

### Post by philinux on 2010-11-16
Does anything remain of your changes to ubuntu when you reboot. e.g documents, drivers, appearance etc. If so then persistence is enabled.

Also at login you need to select the Session. Desktop or remix etc. Or it will remain at the default of remix.

---

### Post by Avidanborisov on 2010-11-17
> **philinux said:**
> Does anything remain of your changes to ubuntu when you reboot. e.g documents, drivers, appearance etc. If so then persistence is enabled.

Also at login you need to select the Session. Desktop or remix etc. Or it will remain at the default of remix.

Nothing is saved and I don't have the login screen. It just logs on automatically into ubuntu.

---

