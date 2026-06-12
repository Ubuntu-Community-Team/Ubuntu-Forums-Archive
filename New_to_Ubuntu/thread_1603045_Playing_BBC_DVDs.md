---
title: "Playing BBC DVDs"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by Ustonkey on 2010-10-22
I'm new to UBUNTU, (86 years old and a bit thick!)
  I have some BBC video DVD's, Can i play them on my computer?.
  They seem to come up with an error when I try them. OK on my TV.
   Ustonkeyhttp://ubuntuforums.org/images/smilies/confused.gif

---

### Post by cascade9 on 2010-10-22
Do you DVDcss installed? 

> **Installing libdvdcss**

 Legal Warning: Check with your local laws to make sure usage of libdvdcss2 would be legal in your area. 
 
**Ubuntu 9.04, 9.10 and 10.04 (i386, amd64)**

 
[LIST]
[*]Install the **libdvdread4** package (**no need to add third party repositories**) via Synaptic or command line: 
[/LIST]

 sudo apt-get install libdvdread4
[LIST]
[*]Then open a terminal window and execute: 
[/LIST]

 sudo /usr/share/doc/libdvdread4/install-css.sh
[LIST]
[*]Rebooting may be necessary. 
[/LIST]
 


[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

If that isnt the issue you are having, then a bit more information (like the actual error msg) would be a good idea ;)

---

### Post by Grenage on 2010-10-22
> **Ustonkey said:**
> I'm new to UBUNTU, (86 years old and a bit thick!)
  I have some BBC video DVD's, Can i play them on my computer?.
  They seem to come up with an error when I try them. OK on my TV.
   Ustonkeyhttp://ubuntuforums.org/images/smilies/confused.gif

At 86, I commend you for switching to something so different!  **Cascade**'s advice is great; I'd actually go one step further and just install all of the restricted extras:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Ustonkey on 2010-10-22
H[COLOR="black"][SIZE="6"]

[/SIZE][/COLOR]Hi Cascade9,
                           Many,many thanks for your assistance your  fix solved my problem. I do try to solve my own problems by looking in the forums and in books, and many times I am successful, but I don't think I could have solved this one. I've never heard of "libdvdread4"http://ubuntuforums.org/images:)
  Thanks once again,
  Ustonkey

---

### Post by cascade9 on 2010-10-23
Glad it worked ;) 

I dont know, you might very well have solved it youself.

You didnt actually need to find "libdvdread4" exactly..... Searching "ubuntu DVDcss" in a internet search engine gets you to the same page I linked you to. 

The only trick is knowing that DVDcss is something you need to have to play encrypted DVDs.

---

