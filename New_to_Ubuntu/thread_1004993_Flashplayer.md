---
title: "Flashplayer"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by cs_1939 on 2008-12-07
How do I get flashplayer to work in Firefox?:confused:

---

### Post by mikewhatever on 2008-12-07
> **cs_1939 said:**
> How do I get flashplayer to work in Firefox?:confused:

What do you mean?

---

### Post by Bölvaður on 2008-12-07
you need to install flash... the package that comes from adobe that is here is called flashplugin-nonfree

Follow my lead:

System &#8594; Administrator &#8594; Synatpic Package Manager
Insert your password
Look for "flashplugin-nonfree"
Mark for installation, click apply, accept the changes.


or copy this to the terminal (Applications &#8594; Accessories  &#8594; Terminal)
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by ces1939 on 2008-12-08
Thanks, I am sure that will solve the problem in Ubuntu. Now all I have to do is figure out how to get it to work in Firefox on XP.:popcorn:

---

### Post by cs_1939 on 2008-12-12
Thanks for the help!!!

---

### Post by suncoolsu on 2008-12-13
If u use 64 bit ubuntu - us shd install the 64 bit flash player released recently by Adobe

---

### Post by lmworthen on 2008-12-14
how do those of us using xubuntu get flashplayer?

---

### Post by kansasnoob on 2008-12-14
> **lmworthen said:**
> how do those of us using xubuntu get flashplayer?

Start by installing:

```
sudo apt-get install xubuntu-restricted-extras
```

Afterwards restart Firefox by going to File > Quit.

I've also found that flashblock is a true advantage (it replaces the flash screen with a "button". It's in the repos also.

---

