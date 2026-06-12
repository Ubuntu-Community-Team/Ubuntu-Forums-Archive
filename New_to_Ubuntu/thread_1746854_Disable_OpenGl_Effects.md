---
title: "Disable OpenGl Effects"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by Arifcatalyst on 2011-05-02
umm. I am UsiNg UbuNt V11.04desktop-i386

I am Unable To LOgin Through nOrmal effects...WHenever I try To LogiN I get Weird Screens

Well!!! maybe my Gpu Isnt MucH Better. So I had To Switch Ubuntu classic(no effects)!!!

 BUt The ProBLeM Still Persists!!!

HEre Z THE SS
[IMG]http://i51.tinypic.com/2s6uaza.png[/IMG]


WatcH The BlacK Lines!!!! ????

So I Googled And I think So The PRoblem IS wid OPenGl!!!

Earlier I Was Using ubuntu v10 ANd Whenver I Try To opEn CAiro-docK With OpenGl. I get ThE same Sh*t Screen

I HAve Narrowed i!!! after SearchINh hrs!!!

Plzz HelP ME ANy1

And YEah Some MAy Argue That Install A fresh InstallatioN AS I Am UsiNg Through Wub!!!

I tried al Possibilities BUt It DoesnT resolvE!!!

---

### Post by kaldor on 2011-05-02
That looks really bad. Which graphics card do you have? Run this in Terminal (Applications > Accessories > Terminal):

```
lspci | grep VGA
```

This will give you the type of graphics card you have. Mine says [I]01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
[/I], and you should see something similar.

You should see if there are any proprietary drivers available. Go to System > Administration > Additional Drivers and see if there's anything there.

---

### Post by Arifcatalyst on 2011-05-02
> **kaldor said:**
> That looks really bad. Which graphics card do you have? Run this in Terminal (Applications > Accessories > Terminal):

```
lspci | grep VGA
```This will give you the type of graphics card you have. Mine says [I]01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
[/I], and you should see something similar.

You should see if there are any proprietary drivers available. Go to System > Administration > Additional Drivers and see if there's anything there.
It Says "No Proprietary DrivErs Availabe for Your System!!!

SOmebody helP ME OuT of Thsi Jam ;'(

---

