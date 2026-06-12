---
title: "Eee Pc Sound Problems..."
date: 2009-02-17
forum: New to Ubuntu
---

### Post by LazyLlama on 2009-02-17
I recently installed Ubuntu onto my Eee pc 701. But, to my disappointment, the sound it produces is really, really quite. Even though I've turned the system's sound up and Ubuntu's sound up but still not much different.
  Amarok says somthing about the fact my sound drivers arn't working.

If this is the case, how do I fix it?

Any help will be much appreciated!

(Although I don't think it matters too much, I'm using Eeebuntu)

---

### Post by DerHesse on 2009-02-17
Hola Layzellama,
 
EEEbuntu: You are using the kernel from array.org.
Have a look here: [http://array.org/ubuntu/status.html?model=eeepc-701SD](http://array.org/ubuntu/status.html?model=eeepc-701SD) .
As ist seems your hardware is not well supported but should work. 
 
Try 
$ alsamixer 
and see if you can make changes there.
 
Greetz
 
My Sound from eeepc 901 (same Sound Card as yours) is working ok, but is not very loud. I am using this kernel as well.
 
 
EDIT:// found something else which makes sound much louder:   gnome-volume-control

---

### Post by Temposs on 2009-02-17
Try these fixes for common issues with Ubuntu EEE/Easy Peasy(the latest version):

[http://www.ubuntu-eee.com/forum/viewtopic.php?f=12&t=543](http://www.ubuntu-eee.com/forum/viewtopic.php?f=12&t=543)

EDIT: Pay special attention to number 4, as it is exactly the issue you're having.

---

### Post by Temposs on 2009-02-17
Also, it does matter that you're using ubuntu-eee. You should go ask your questions on the ubuntu-eee forums, especially for hardware and eeepc and netbook issues, and you will consistently get more focused help with your particular distribution.

Ubuntu-eee is now known as Easy Peasy and is a proper distribution.

[http://www.geteasypeasy.com/](http://www.geteasypeasy.com/)

---

### Post by LazyLlama on 2009-02-17
Thanks for the help guys,
  I'll try some now :D

Actually, I'm not using ubuntu-eee, its Eeebuntu, which I think is pretty different.

---

### Post by DerHesse on 2009-02-25
> **LazyLlama said:**
> Thanks for the help guys,
  I'll try some now :D

Actually, I'm not using ubuntu-eee, its Eeebuntu, which I think is pretty different.

As regards the kernel, they are just the same.
Both use arry.org's kernel. ;)

EDIT:// have you tried gnome-volume-control allready ?

---

### Post by sd_alby on 2009-03-12
Just purchased eeePC 1000. Loaded eeebuntu 2.6.27-eeepc. Again, very low sound, no static, tried to gedit /etc/default/eeepc-config but no file of that name in directory. eee-control-daemon version: 0.8.3 installed and also distro came with eee-config which most of the scripts don't work. When I test sound in preferences - sound, it is good, loud, tone. The online video or media files cannot even hear them, very low. Unusual to get one but not the other, newb to Ubuntu is more than likely the iss

never mind, got it fixed. Did the 
Try these fixes for common issues with Ubuntu EEE/Easy Peasy(the latest version):

[http://www.ubuntu-eee.com/forum/view...php?f=12&t=543](http://www.ubuntu-eee.com/forum/view...php?f=12&t=543)

EDIT: Pay special attention to number 4, as it is exactly the issue you're having.
2nd time it worked.

---

