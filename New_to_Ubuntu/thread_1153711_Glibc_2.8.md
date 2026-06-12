---
title: "Glibc_2.8"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by navaneethan on 2009-05-09
Hai Friends,

            I am using ubuntu 8.04 ,i have installed some packages in my system which are installed in ubuntu 8.10

Click for more details [HERE]("http://navaspot.wordpress.com/2009/04/16/some-problem-in-my-hardy/")

Now i am in GLIBC problem if you know any idea you can share with me

---

### Post by sankarv on 2009-05-09
hi,

it seems you have some library incompatibilities since you have a mix up of intrepid into hardy as it will ad some new libs. i suppose apart from glib it may affect other apps/libs too.... best thing is to backup your data and reinstall intrepid probably.... for no more confusion..... well its up to you.. i jus stated what i would hav done......

---

### Post by Didius Falco on 2009-05-09
You could try and save that install by booting into **Recovery Mode** and choosing the **Command Line with Network Support **option at the choices screen.

Once at the command line,navigate to that folder and run ```
sudo dpkg -r *.deb
```

Then reboot and see if it loads. If it doesn't, reboot again and go back into the **Command Line with Network Support **option and run ```
sudo dpkg -p *.deb
```

Watch the output carefully both times - I've no idea what you installed, so I can't say what it would remove. If you see a lot of essential stuff like your desktop file being removed, you can try to reinstall them.

This is all a longshot, though. Your best bet would be to use a Live CD to backup your data and re-install. You could borrow your friends Intrepid CD and install that, or have him burn you one of your own.

Good Luck!!

Regards,

Didius

---

