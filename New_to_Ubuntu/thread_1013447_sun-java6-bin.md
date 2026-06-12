---
title: "sun-java6-bin"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by zubaer on 2008-12-16
im trying to install Skype on my dell mini (installed 8.10 today). In the installing dependencies section, it has been stuck on "preparing sun-java6-bin" for about 30 minutes. I'm assuming i need to do something different. any ideas? thanks!

---

### Post by iaculallad on 2008-12-16
Try reading this [page]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins#Java") from the Ubuntu Community.

HTH.

---

### Post by starcannon on 2008-12-16
Is this the default Dell Ubuntu installation on your mini9?

If your doing your own Ubuntu install on the mini9 perhaps install java first then install skype after.

```
sudo apt-get install ubuntu-restricted-extras
```
that will grab sun-java6 as well as a heap of other very useful add-ons.

GL

---

### Post by kostkon on 2008-12-16
> **zubaer said:**
> im trying to install Skype on my dell mini (installed 8.10 today). In the installing dependencies section, it has been stuck on "preparing sun-java6-bin" for about 30 minutes. I'm assuming i need to do something different. any ideas? thanks!
Try pressing the *Details* arrow button because you need to agree to a Sun license.

---

### Post by iaculallad on 2008-12-16
> **kostkon said:**
> Try pressing the *Details* arrow button because you need to agree to a Sun license.

Or you have to press the TAB key to select the OK button on the agreement page.

HTH.

---

### Post by zubaer on 2008-12-16
It had to do w/ "sudo apt-get install ubuntu-restricted-extras".  I had attempted to install it earlier but got confused at the screen where i had to tab to press OK! I really appreciate the help...3 hours in and I'm learning so much already! Thanks!:D

---

