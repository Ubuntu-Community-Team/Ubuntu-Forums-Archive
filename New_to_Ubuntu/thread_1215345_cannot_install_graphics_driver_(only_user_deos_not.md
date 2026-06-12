---
title: "cannot install graphics driver (only user deos not have &quot;Administrative Privileges&quot;)"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by GribbleMR2 on 2009-07-17
*BACKSTORY, not pertinent to problem* 
So, I made the mistake of giving my mom my password so she could access our windows partition from Ubuntu while I was away.  She then ran Kleansweep and destroyed Ubuntu so I reinstalled 8.04 without formatting the partition so as not to lose everything.

*PROBLEM NEED HELP*

After a clean install (without formatting), I ran the updater and was about to install my graphics driver (ATI restricted driver) and when I click the "enable" I get a pop up that says "Starting without Administrative Privileges"

I am the only user, and have restricted software enabled in the software sources menu.

It does not prompt me for my sudo password. 

Any ideas why I cannot install my graphics driver?

---

### Post by j7%&lt;RmUg on 2009-07-17
Im a little confused about where you clicked "enable"?

If you provide a more informative description of the problem then i am willing to help you more.

---

### Post by GribbleMR2 on 2009-07-17
Sorry, I should have clarified that a bit.  I checked the box correlating to my grahics driver in the "Hardware Drivers" manager (System-Administration-Hardware Drivers) and then clicked "enable" in the confirmation box that followed.  That is when I got the error message.  If you need any more info, just ask.

Thanks

---

### Post by GribbleMR2 on 2009-07-17
Bumb for day crew

---

### Post by Tman5293 on 2009-07-17
You can fix this problem by going to terminal and typing: "sudo jockey-gtk" (without quotes)

---

### Post by iamkrazee on 2009-07-17
If above fails, report back with the output of the following
```
sudo jockey-gtk --list
```

---

### Post by GribbleMR2 on 2009-07-17
Thanks, that worked

---

