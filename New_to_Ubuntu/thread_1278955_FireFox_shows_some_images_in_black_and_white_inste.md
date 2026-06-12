---
title: "FireFox shows some images in black and white instead of real colors?"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by legolas_w on 2009-09-30
Hello everyone.

I have a problem with Firefox :O.
It shows some of the images in the net in black and white instead of showing them in the correct color :O

For example, the first photo shows FF 3.5.3 rendering the [http://www.engadgetmobile.com/2009/09/10/motorola-cliq-first-hands-on-impressions/](http://www.engadgetmobile.com/2009/09/10/motorola-cliq-first-hands-on-impressions/) and the second photo shows how Opera render the same page.

Any clue?

FireFox 3.5.3
[[IMG]http://img2.tinypic.info/files/vsxz92nti7uayvpy2a9f_thumb.png[/IMG]](http://img2.tinypic.info/viewer.php?file=vsxz92nti7uayvpy2a9f.png)

Opera 10
[[IMG]http://img2.tinypic.info/files/79sg5agq2i459ferr82p_thumb.png[/IMG]](http://img2.tinypic.info/viewer.php?file=79sg5agq2i459ferr82p.png)


Thank you for your attention.

---

### Post by halitech on 2009-09-30
strange, it loads properly for me in ff 3.0.6 on debian.

what happens if you load just the image in ff?

[http://www.blogcdn.com/www.engadget.com/media/2009/09/cliq-demo-3-sm.jpg](http://www.blogcdn.com/www.engadget.com/media/2009/09/cliq-demo-3-sm.jpg)

---

### Post by legolas_w on 2009-09-30
Hi,
Opening the image directly results in a  black and white one :(
Thanks

---

### Post by halitech on 2009-09-30
strange.... you say it is only some images? are the images all jpgs? (right click - properties on the image to find out) or do some jpgs show up properly and it is other types that don't show properly?

---

### Post by legolas_w on 2009-09-30
Hi
I tested with some gif files and they are ok, like the smillies in "new post" section of this forum. I also checked with some JPG files located at: [http://www.gsmarena.com/motorola_dext_mb220-pictures-2934.php](http://www.gsmarena.com/motorola_dext_mb220-pictures-2934.php) and they are fine. but some times it does not show the colors properly.

I am really amazed and also confused.

---

### Post by halitech on 2009-09-30
doesn't make much sense, maybe its a bug with the way it renders certain types of jpgs based on how they are created

---

### Post by lovinglinux on 2009-09-30
It's due to color management. See **Solution** [*[COLOR="Red"]**FOT007**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT007).

---

### Post by CaptainMark on 2009-09-30
black and white are both real colours

---

### Post by legolas_w on 2009-10-01
> **lovinglinux said:**
> It's due to color management. See **Solution** [*[COLOR="Red"]**FOT007**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT007).

Thank you very much.

It is solved now.

---

