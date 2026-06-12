---
title: "I can't find a program I installed? And a few other quick q&amp;a :D"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by baloonce on 2009-03-02
Hi guys,

I have installed AIM messenger and I can't find it to use! It has been installed - I checked that in Synaptic.

Also, I installed that because I'm trying to use webcam chat and have had a few troubles so if anyone can help me that would be great.

I've got a generic webcam - 480k (whatever that means) which works fine on ekiga - but i dont' know how to use that as my friend is on skype and AIM?

So i tried skype but my image either comes up as a green staticy screen or the image is there but its completely green.

Does anyone have a simple way i can use a webcam chat??

---

### Post by Xiong Chiamiov on 2009-03-02
```

dpkg-query -L [package name]

```
should list the files installed by that package.

---

### Post by baloonce on 2009-03-02
> **Xiong Chiamiov said:**
> ```

dpkg-query -L [package name]

```
should list the files installed by that package.
Thanks - I did that and it has listed all the files - now what do i do? I'm clearly an ABSOLUTE beginner - if it doesnt work like windows then i dont yet know what to do.

---

### Post by sandyd on 2009-03-02
```

/usr/local/bin/aim

```

welcome to ubuntu and congrats on running your first program from the terminal ! :)

(you can also create your own menu shortcut for it)

---

### Post by sandyd on 2009-03-02
looks like somethings wrong with the webcam color profile in skype....

---

### Post by baloonce on 2009-03-03
> **carlee said:**
> ```

/usr/local/bin/aim

```

welcome to ubuntu and congrats on running your first program from the terminal ! :)

(you can also create your own menu shortcut for it)

Thanks Carlee! Ok, - i tried that - it didn't work - does that mean i need to re-install it? This is what came up in the terminal:

~$ /usr/local/bin/aim
/usr/local/bin/aim: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

Now, the webacm colour profile in Skype - i can't work out how to do that - i know these sound like dumb questions but i've spent days trying to work it out!

---

