---
title: "Ubuntu 10.04- Moving exit buttons to right"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by sodra on 2010-04-29
Hi
When I installed 10.04, I restarted, logged in, and found that the exit buttons on application windows were on the left now!
How do I put the Exit and minimise buttons to the right again?

---

### Post by howefield on 2010-04-29
Posts all over the forum regarding this point... eg.


[http://ubuntuforums.org/showthread.php?t=1434658](http://ubuntuforums.org/showthread.php?t=1434658)

---

### Post by linuxman94 on 2010-04-29
Download the attached file and then right click it.  Select properties and then the tab permissions.  Make sure the box for allowing it to be executed is checked.  Close the properties dialog, double click the scrip and select run. You will be able to change the button positions.

---

### Post by cariboo on 2010-04-29
If you use any other theme but Radiance or Ambiance, the buttons will be on the right (the old fashioned way) :)

---

### Post by howefield on 2010-04-29
> **cariboo907 said:**
> If you use any other theme but Radiance or Ambiance, the buttons will be on the right (the old fashioned way) :)

This was my understanding, but seeing a couple of threads last night and trying it myself, Dust also has buttons on the left.

---

### Post by Gargoulf on 2010-07-07
type gconf-editor in a terminal
apps > metacity > general

right-clic on button_layout and select "edit key"
change value to 
":minimize,maximize,close"  (without the quotes)

that's it!

---

### Post by twizler on 2010-08-05
> **cariboo907 said:**
> If you use any other theme but Radiance or Ambiance, the buttons will be on the right (the old fashioned way) :)

Just click -- System--? Preferences --> appearance --Theme -- and pick one -- in the boxes 

clearlooks 
Darktheme 
 

OR ANY OTHER  and presto the close - maximize - and minimize buttons in Ubuntu 10.04 are on right side -- as normally is on 99% of every OS  :popcorn:

---

### Post by cjack007 on 2010-08-06
just install ubuntu tweak. 

in it there is a option that where we want our buttons to be placed right or left just select appropriate option done ......

easiest way

---

### Post by zorrito_1978 on 2010-09-21
> **Gargoulf said:**
> type gconf-editor in a terminal
apps > metacity > general

right-clic on button_layout and select "edit key"
change value to 
":minimize,maximize,close"  (without the quotes)

that's it!

that's the way!
thanks

---

### Post by JungleFish on 2011-03-23
> **linuxman94 said:**
> Download the attached file and then right click it.  Select properties and then the tab permissions.  Make sure the box for allowing it to be executed is checked.  Close the properties dialog, double click the scrip and select run. You will be able to change the button positions.

You sir, are the man. So easy so simple, I love it.

---

### Post by yaobikuni on 2011-05-29
> **linuxman94 said:**
> Download the attached file and then right click it.  Select properties and then the tab permissions.  Make sure the box for allowing it to be executed is checked.  Close the properties dialog, double click the scrip and select run. You will be able to change the button positions.

Efficient and lovely. Thank you.

---

### Post by benpack101 on 2011-05-29
You may also want to look at Ubuntu Tweak.
It is a nice program that'll let you edit tons of different things in Ubuntu

---

