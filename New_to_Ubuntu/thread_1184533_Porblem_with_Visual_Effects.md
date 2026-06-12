---
title: "Porblem with Visual Effects"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by alket on 2009-06-11
In Intrepid Ibex my visual effects supported The Normal and Extra options
but now in Jaunty it doesn't work with both of them , just None.

The output of:
lspci | grep VGA
> 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)


---

### Post by pmlxuser on 2009-06-11
try to manually download and install the display driver. I think an updated version is available either form the intel website or in ubuntu repository.

(basically uninstall the interl display driver and update the display drivers)

---

### Post by alket on 2009-06-11
> **pmlxuser said:**
> try to manually download and install the display driver. I think an updated version is available either form the intel website or in ubuntu repository.

(basically uninstall the interl display driver and update the display drivers)

How to do that ?

---

### Post by reeseslover531 on 2009-06-11
check [this]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821") bug out that seems to be your issue.

---

### Post by alket on 2009-06-11
So I guess I have to wait till they fix it.

---

### Post by baucha_linux on 2009-06-11
I think this is what u need.

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

follow the steps very carefully.

---

### Post by alket on 2009-06-11
> **baucha_linux said:**
> I think this is what u need.

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

follow the steps very carefully.

too confused for me :S

---

### Post by baucha_linux on 2009-06-15
> **babaroga said:**
> too confused for me :S

Just follow the Part A and Part B of the tutorial in that forum. U forget the rest. That way u will get the latest intel driver.

The directions there are pretty forward. Just stick for the safe mode, no need to try for optimal or bleeding edge.

Hope it helps.

---

### Post by alket on 2009-06-16
I tried that but didnt work.

Do you think reverting to the intrepid version of the driver is a Problem ?

[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance#Reverting%20to%20the%20intrepid%20version%20of%20the%20driver](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance#Reverting%20to%20the%20intrepid%20version%20of%20the%20driver)

---

### Post by treesurf on 2009-06-16
There is no harm in trying to revert to the Intrepid driver. For some intel chips it solves the problem, for others it doesn't.  If reverting does not work then I would recommend at least trying the optimal fix in the Howto thread.  The directions are fairly simple and if you don't like the results there are instructions on how to revert to the default Jaunty installation.  Good luck!

---

