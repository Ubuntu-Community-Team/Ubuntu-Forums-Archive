---
title: "unable to extract the files  .gtgz"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by legy on 2011-04-04
I'm unable to extract the files .gtgz .
the error is :** An error occured while extracting these files**. 

I have downloaded these files many times to check whether it is the problem with downloading.
Each time it is the same error.

Please help!!


I recently started with  ubuntu - (maverick) and want to kick start with OpenFOAM (cfd software).

these .gtgz files are from the 
[http://www.openfoam.com/download/source.php](http://www.openfoam.com/download/source.php)


Sorry!! dono how to start of with a new thread

---

### Post by QLee on 2011-04-04
> **legy said:**
> I'm unable to extract the files .gtgz .
the error is :** An error occured while extracting these files**. 

I have downloaded these files many times to check whether it is the problem with downloading.
Each time it is the same error.

Please help!!


I recently started with  ubuntu - (maverick) and want to kick start with OpenFOAM (cfd software).

these .gtgz files are from the 
[http://www.openfoam.com/download/source.php](http://www.openfoam.com/download/source.php)


Sorry!! dono how to start of with a new thread

A quick search of the forums suggested:
[https://help.ubuntu.com/community/OpenFOAM](https://help.ubuntu.com/community/OpenFOAM)

Looking at the top of that page suggests:
[http://www.openfoam.com/download/ubuntu.php](http://www.openfoam.com/download/ubuntu.php)

Maybe that would be the way to proceed.

---

### Post by andrew.46 on 2011-04-04
> **legy said:**
> I'm unable to extract the files .gtgz .
the error is :** An error occured while extracting these files**. 

[...]

these .gtgz files are from the 
[http://www.openfoam.com/download/source.php](http://www.openfoam.com/download/source.php)

Seems a little odd, the first of the files extracted fine here using the following syntax:

```

tar xzvf OpenFOAM-1.7.1.gtgz

```

Mind you there are specific instructions for Ubuntu here which might serve you better:

[http://www.openfoam.com/download/ubuntu.php](http://www.openfoam.com/download/ubuntu.php)

as QLee has suggested...

---

### Post by legy on 2011-04-05
i followed the first two steps of the link on openFOAM u have given .

after that it asks for password in the terminal.


**[sudo] password for legy:**

and i m unable to enter anything except **ENTER** key and it says

**Sorry ,try again**:

---

### Post by Daniel0108 on 2011-04-05
> **legy said:**
> i followed the first two steps of the link on openFOAM u have given .

after that it asks for password


**[sudo] password for legy:**

and i m unable to enter anything except **ENTER** key and it says

**Sorry ,try again**:

This is a security function, instead of typing ***** it just types nothing. Just type in your password and press enter, it'll work ;)

Yours,
Daniel

---

### Post by legy on 2011-04-07
Thank you all . 
finally the installation is done!

---

