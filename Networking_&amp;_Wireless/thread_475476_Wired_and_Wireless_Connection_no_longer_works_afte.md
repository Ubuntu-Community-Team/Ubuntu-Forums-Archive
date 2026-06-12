---
title: "Wired and Wireless Connection no longer works after some updates..HELP!!!"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by ryeyan on 2007-06-16
im quite a noob of linux..n hav bin a ubuntu user for less than a month..ive been downloading a lot of packages and updates lately..

the last time i updated was on june 9, 2007..now im really having problems with my network connections..i didnt have these problems before i last updated..now i can't seem to connect to the internet ..xet..

i usually set my wired connection to static with the given ips at school..and my wireless just to roaming..ubuntu recognizes my drivers but it really can't connect to the internet..arrgh..i was hoping my relationship with ubuntu would work out fine coz i fine this os quite interesting than other linux flavors..hope u guys out there could help me out..

HELP!!:(

---

### Post by ryeyan on 2007-06-16
my laptop is a toshiba L100 with intel wireless and realtek ethernet...

network connections work real fine at first..now its just xet..arrrgh..
dont really know what caused this..totally noob at th

---

### Post by growler on 2007-06-16
ryeyan

 I've experienced the same problem after kernel updates 2 weeks ago.

After booting run [COLOR="Red"]sudo /etc/init.d/networking restart[/COLOR]... this connects my wireless just fine.

Atheros AR5005G 802.11abg NIC

WPA/PSK setup as per sticky above


growler

---

### Post by ryeyan on 2007-06-17
hope this works..
hav to check it on my laptop..

bin using a different pc..
tnx..

il be posting nxt tym if this works or not..

---

### Post by ryeyan on 2007-06-17
does the ubuntu people know updates messes up your network connections?

---

### Post by growler on 2007-06-17
yep, there is a bug.

 Did the restart get your wirelrss going??

growler

---

### Post by ryeyan on 2007-06-18
nope..

it hasnt fix anything..

is there any other solution to these problem?

i really appreciate the help..

---

### Post by ryeyan on 2007-06-21
ei, any1 got a soln to this problem?

or do i rili hav to reinstall ubuntu?

..crap.

---

### Post by wieman01 on 2007-06-21
Could you not simply boot your PC using the previous version of your kernel? It should appear in GRUB. Just don't select the most recent version that has messed with your network interfaces.

---

### Post by ryeyan on 2007-06-23
yup..tried booting the old kernel..
doesnt work either..tsk2

---

### Post by ryeyan on 2007-07-03
i hav reinstalled ubuntu..
plan to update the os..

does the update still mess with the network?

---

