---
title: "DVD &amp; Dialup Internet Set-up"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by drneals on 2008-12-15
I just purchased a Dell Mini 9 running Ubuntu 8.04.  Even though I have worked with computers since 1964 I am new to the Linux world. The instruction book does not provide info on how to get the CODECS for the DVD player and there are no instructions for setting up a dial-up modem (a new one capable of doing Linux).  Any help pointing me to directions to do these two things will be most appreciated.

---

### Post by oldos2er on 2008-12-15
For codecs, see [http://medibuntu.org/](http://medibuntu.org/)

 And for dial-up: [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

---

### Post by om1 on 2008-12-15
for dvd's and other multimedia try out [http://www.medibuntu.org/](http://www.medibuntu.org/)
it provides codecs for ubuntu

---

### Post by Izek on 2008-12-15
For Codecs:

in terminal

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

then

```
sudo apt-get update
```

then

```
sudo apt-get install medibuntu-keyring
```

then

```
sudo apt-get update
```

then For i386 Users install Codecs using the following command

```
sudo apt-get install w32codecs libdvdcss2
```

Or for x64 users

```
sudo apt-get install w64codecs libdvdcss2
```

remove the medibuntu from the software sources (System > Administration) after, DO NOT update anything that is added to the update manager by medibuntu (You won't be able to tell if they are in the update manager by the way.)

---

### Post by drneals on 2008-12-15
I tried the dialer recommendations.  It appears Dell has locked down the Administration - Network.  So, I tried using the alternative way (using svdialconf, etc.  things looked good until it did not take the recommeded nano command.  I am new to Linux but in the past, the old days, I did set up modems.  Help!!

---

