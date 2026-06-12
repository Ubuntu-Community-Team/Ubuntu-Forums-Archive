---
title: "karmic 64 live cd"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by DarinB on 2009-11-05
i decided to try karmic live cd it booted fine but could not go online with it???
screen res was good and everything else seemed to work.
any ideas. don't want a headache when i can go i386 or easily wait for a few months after lynx comes out and all the bugs are clear. getting tired of the twice a year upgrade looking to move to lts and just be a happy user

---

### Post by RedSingularity on 2009-11-06
What is your output of lspci?

---

### Post by DarinB on 2009-11-06
can i check that on a live cd???

---

### Post by RedSingularity on 2009-11-06
Sure.  Just open a terminal and punch it in.

---

### Post by waspbr on 2009-11-06
to open a terminal window just go to Applications > Accessories > Terminal

---

### Post by lavinog on 2009-11-06
> **DarinB said:**
> i decided to try karmic live cd it booted fine but could not go online with it???


Are you trying to go online using a wireless connection, or a wired connection?
Wireless connections are weird on the live cd because not all hardware vendors allow ubuntu to be packaged with the drivers.  This is a legal issue, and should be taken up with your vendor.

After the install you should be able to download and install the driver.

---

### Post by DarinB on 2009-11-07
no i am trying the live cd to see if it will work before i install. i will try a 32bit version to see if it is a karmic issue in general or a karmic-64bit issue alone. i haven't had a time to restart the pc with the disk it is a pain since i can't access the forum to work the problem. Since online access is the issue. 
I am using a wired connection.

---

### Post by lavinog on 2009-11-07
what network card do you have?

---

### Post by RedSingularity on 2009-11-07
> **lavinog said:**
> what network card do you have?


lspci will give that information.

---

### Post by Paqman on 2009-11-07
> **DarinB said:**
> no i am trying the live cd to see if it will work before i install. i will try a 32bit version to see if it is a karmic issue in general or a karmic-64bit issue alone.

If your network interface needs a proprietary driver you won't be able to get online using the LiveCD, whether 32-bit, 64-bit, Karmic or Jaunty. The system should prompt you if a restricted driver is required.

---

### Post by RedSingularity on 2009-11-07
> **Paqman said:**
> If your network interface needs a proprietary driver you won't be able to get online using the LiveCD, whether 32-bit, 64-bit, Karmic or Jaunty. The system should prompt you if a restricted driver is required.


And, like paqman said, you can find the option to do that in System>Admin>Hardware Drivers

---

