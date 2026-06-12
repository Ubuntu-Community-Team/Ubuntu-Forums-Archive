---
title: "modprobe ndiswrapper returns error"
date: 2005-08-24
forum: Networking &amp; Wireless
---

### Post by bart416 on 2005-08-24
I have a topcom USB SkyR@cer V2 54mbps wireless network device/crap.
Since topcom doesn't make linux drivers.
For people intrested, this is the response of topcom on my second request for linux drivers:
> 
Dear Sir,

Topcom is a company which manufactures products for a large customer group.
We want our prices to be very attractive so we must make choices.  We
therefore choose to focuss on Windows based products because our typical
customer is someone who want's to buy a good product for a reasonably low
price.  
There are other brands which are much more expensive but who have different
target groups like Mac or Linux users and they focuss ons drivers and FW for
these users.  I understand from your mail you are a Linux fan and as much as
I would like to help you, I'm afraid we will not be able to since our
corporate strategy is to focuss on mainstream products.


Best regards,
 

So those are not goign to help me.
Then somebody told me about NDISWrapper.
So i installed ndiswrapper-utils from my cd.
Next i got the drivers from my windows.
The drivers are: SiS163u

So i copied the dir with the drivers (named SiS163u) from my windows partition to my linux partition. The driver files are in: /home/bart/windows_drivers/SiS163u/WinXP/

Driver file name: sis163u.inf (the .sys and .dll files are included)

So i got started with
```

ndiswrapper -i  /home/bart/windows_drivers/SiS163u/WinXP/sis163u.inf
ndiswrapper -l

``` 

That returned
```

Installed ndis drivers:
sis163u driver present, hardware present
[CODE]

So i continued with:
[CODE]
ndiswrapper -m

```

and then:
```

root@ubuntu:/home/bart # modprobe ndiswrapper
FATAL: Error Installing ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko):operation not permitted

``` 
(written over to a paper so their might be writing mistakes)

So i  didn't realy panic and i tried to use the hotplug system (since somebody adviced me to use that if modprobe didn't work).
i did ndiswrapper -hotplug
No errors returned...
So i tought, must be installed fine then.
So i added ndiswrapper to the /etc/modules file

Now when i boot to ubuntu it stops loading at the hotplug system.
I have next linux cd's (maybe i can fix it with one of them):
knoppix
ubuntu 5.04 live cd
ubuntu 5.04 installation cd
mandrake linux 10.1

grub boot options:
ubuntu linux
ubuntu linux (recovery)
win xp pro

Can anybody help me with this?

---

### Post by s_p_a_r_k_y on 2005-08-24
yea take it out of the modules file with one of your live cds. I don't have experience with your USB wireless card, but ndiswrapper helps in a lot of places but also causes a lot of headaches. I usually recommend trading it with someone who has a devices you konw will work on Linux or returning it and supporting products which have Linux support. However if thats not an option, how did you install ndiswrapper? Did you get it through apt or did you compile it yourself?

---

### Post by humanity_to_others on 2005-08-24
If you have a 64 bit system then you can't use 32 bit drivers. More info there:
[http://ubuntuforums.org/showthread.php?t=15425&highlight=SiS163u](http://ubuntuforums.org/showthread.php?t=15425&highlight=SiS163u)

---

### Post by bionnaki on 2005-08-25
see this thread: [http://www.ubuntuforums.org/showthread.php?t=59406](http://www.ubuntuforums.org/showthread.php?t=59406)

I had the same trouble. try what I did.
good luck.

---

### Post by bart416 on 2005-08-25
[QUOTE=humanity_to_others]If you have a 64 bit system then you can't use 32 bit drivers. More info there:
[http://ubuntuforums.org/showthread.php?t=15425&highlight=SiS163u](http://ubuntuforums.org/showthread.php?t=15425&highlight=SiS163u)[/QUOTE]
Last time i checked celeron 1.1ghz cpu's are 32bit :P

I did use the instructions in the wiki, didn't compile it myself.

The problem will be getting the new ndiswrapper-utils on my comp.
I can only hardwire it to the router if parents are not home because they hate it when i take my pc downstairs.

---

### Post by s_p_a_r_k_y on 2005-08-25
bart, what do the last few lines of dmesg say after you try modprobe ndiswrapper?

---

### Post by bart416 on 2005-08-25
i said everything i know.

---

