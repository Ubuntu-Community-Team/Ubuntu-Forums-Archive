---
title: "no video players work for DVDs"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by chapat on 2009-01-01
Hello everyone.

I've run into a problem everytime I try to read DVDs with Ubuntu, and considering my disk drive seems to refuse to work properly in Vista, Ubuntu is my only choice.

I've tried reading with Totem, gxine and VLC but none of these will let me read DVDs. When attempting to use Totem I get a "Could not read from resource" error ; when trying with gxine I get "Segmentation fault" ; and when I try to run it with VLC (using the File/Read DVD(menus) option) VLC just closes after a second.

Before I used to be able to 'detect' the CD with Ubuntu (something Vista refused to do - thus when trying to read a DVD it would say that I was trying to format a blank CD), reboot Vista and read the DVD using VLC. However, when I try that now the images skip and flicker.

Could this be a problem with my disk drive? Even before this problem occurred in Vista I was getting these issues under Ubuntu.

(And I **have** installed 'libdvdread3', by the way)

Thank a lot

-Chase

---

### Post by oilchangeguy on 2009-01-01
> **chapat said:**
> Hello everyone.

I've run into a problem everytime I try to read DVDs with Ubuntu, and considering my disk drive seems to refuse to work properly in Vista, Ubuntu is my only choice.

I've tried reading with Totem, gxine and VLC but none of these will let me read DVDs. When attempting to use Totem I get a "Could not read from resource" error ; when trying with gxine I get "Segmentation fault" ; and when I try to run it with VLC (using the File/Read DVD(menus) option) VLC just closes after a second.

Before I used to be able to 'detect' the CD with Ubuntu (something Vista refused to do - thus when trying to read a DVD it would say that I was trying to format a blank CD), reboot Vista and read the DVD using VLC. However, when I try that now the images skip and flicker.

Could this be a problem with my disk drive? Even before this problem occurred in Vista I was getting these issues under Ubuntu.

(And I **have** installed 'libdvdread3', by the way)

Thank a lot

-Chase

have you considered the probably that you've got a failing dvd drive?

---

### Post by risu_vk on 2009-01-01
seems drive is going off . I faced a similar issue when i kept my dvd drive unused for a long time and then its dvd reading was gone but still used to read /write cds. Is it automounting when you insert the dvd?? i mean can you see the files in nautilus ( explorer).

regards

---

### Post by kansasnoob on 2009-01-01
It could indeed be a drive problem but also you should install ubuntu-restricted-extras either from synaptic or:

```
sudo apt-get install ubuntu-restricted-extras
```

NOTE: of course if this is xubuntu or kubuntu add the x or k:)

And also libdvdcss2 which requires Medibuntu:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by oilchangeguy on 2009-01-01
> **kansasnoob said:**
> It could indeed be a drive problem but also you should install ubuntu-restricted-extras either from synaptic or:

```
sudo apt-get install ubuntu-restricted-extras
```

NOTE: of course if this is xubuntu or kubuntu add the x or k:)

And also libdvdcss2 which requires Medibuntu:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

if it's not working in vista, i doubt it's going to work in ubuntu. the op needs to get another drive to test with.

---

### Post by sadaruwan12 on 2009-01-01
> Could this be a problem with my disk drive? Even before this problem occurred in Vista I was getting these issues under Ubuntu.

Yes you do have an failing drive I've lot of this in my hardware technician days. Most people think it's got to do some thing with the OS but it's not your DVD drives optical pickup lens is loosing it's capability to read DVD's it's better to get new one rather than hanging on to the old one and try to get a DVD-R/RW drive 'cos it's much more versatile than a combo drive or a CD-R/RW and it's worth it.

---

### Post by chapat on 2009-01-02
> **risu_vk said:**
> seems drive is going off . I faced a similar issue when i kept my dvd drive unused for a long time and then its dvd reading was gone but still used to read /write cds. Is it automounting when you insert the dvd?? i mean can you see the files in nautilus ( explorer).

regards
 yes i can, and that's what I find odd: that Ubuntu can 'detect' them and Vista cannot.

[quote=oilchangeguy]have you considered the probably that you've got a failing dvd drive? [/quote]

I had considered the fact that my DVD drive was screwed but I installed Warcraft 3 two days ago (on Vista) after 'detecting' the CD by booting Ubuntu...

I'll give your suggestions a try.

Thanks a bunch :)

---

