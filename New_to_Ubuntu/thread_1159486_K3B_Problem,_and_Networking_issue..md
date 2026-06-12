---
title: "K3B Problem, and Networking issue."
date: 2009-05-14
forum: New to Ubuntu
---

### Post by rokrin on 2009-05-14
Hi there,

To preface this, I am a total ubuntu beginner. I'm learning my way around the operating system and so far I love it, but I'm having a problem that google isn't helping me with now. 

Basically I'm looking to burn an ISO image file to a CD. I've installed the package for K3b, and the program works as far as I can tell, but when it opens I'm getting an error message that says "No CD/Dvd writer was found". I'm using a Dell Inspiron 6400 laptop, and I'm wondering if I missed something I should have done during the installation, but it's not recognizing that my drive has the ability to write discs. Any help with this is appreciated.

I also figured I'd throw this into the same thread but I'm having issues getting Ubuntu to network with my adjacent Windows desktop. I know how to set up windows-windows networks but not linux at all, and if I could do this I could just share the image file with the windows computer and burn it with that. I'm sure it's tiresome to explain that but I'm really bad at forum searching and couldn't find anything, so if there's a link to some kind of guide..that'd be great. I'm running Jaunty Jackalope.

Cheers,
Rokrin

---

### Post by caffienefree on 2009-05-14
If you open up the terminal (Applications>Accessories>Terminal) and issue the command _sudo lshw -C disk_, could you please post the output?

What you're describing regarding the networking sounds like samba. [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by zeroseven0183 on 2009-05-14
Please do what caffienefree is asking so we could have more details about your hardware.

Meanwhile, you can also try the default CD/DVD burner, Brasero. Open it at **Applications > Sound & Video**. You have there options for burning Music, Video, Data and ISO to either CD or DVD.

---

