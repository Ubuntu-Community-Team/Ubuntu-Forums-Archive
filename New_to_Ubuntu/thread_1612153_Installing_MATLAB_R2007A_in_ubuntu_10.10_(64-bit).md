---
title: "Installing MATLAB R2007A in ubuntu 10.10 (64-bit)"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by Boblicol on 2010-11-02
Good day all!

Booting up ubuntu 10.10 (64-bit) and after inserting the MATLAB install DVD and running:

...[dvd]/unix/install.sh

the following is displayed:

> -------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        /media/MATHWORKS_R2007A/unix/update/install/main.sh: 168: /media/MATHWORKS_R2007A/unix/update/bin/glnxa64/xsetup: not found

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

    Sorry! Setup aborted . .

Can anyone shed some light on this?

Regards.

---

### Post by janpol on 2010-11-02
It seems that it can't find the file:

```
/media/MATHWORKS_R2007A/unix/update/bin/glnxa64/xsetup
```

Make shure it's there, otherwise, open a terminal and try to run the terminal version. I think it should go like this:

```
cd ...[dvd]/unix/
sh install.sh -t
```

Hope it helps

---

### Post by beew on 2010-11-02
opps deleted for wrong info.

---

### Post by anewguy on 2010-11-02
Make sure the file is executable as well (chmod +x filename).  Without execute permission it isn't going to run either.

Dave ;)

---

### Post by poiu on 2010-11-09
Hi,

I have exactly the same problem on Ubuntu 10.04. If I type the terminal version of the install this is what I get
```

sudo sh /media/MATHWORKS_R2007A/install_unix.sh -t
awk: linea progr.:2:    BEGIN { found = 0; extra = 9; min = 24; default = 24 }
awk: linea progr.:2:                                            ^ syntax error
awk: linea progr.:6:                if (nrows < min) nrows = default
awk: linea progr.:6:                                         ^ syntax error
awk: linea progr.:12:   END { if (found == 0) print (default - extra) }
awk: linea progr.:12:                                ^ syntax error
awk: linea progr.:12:   END { if (found == 0) print (default - extra) }
awk: linea progr.:12:                                                 ^ syntax error
awk: linea progr.:2: (FILENAME=- FNR=1) fatale: divisione per zero tentata in `%'
[: 582: -le: argument expected

```

while the command 
```

sudo sh /media/MATHWORKS_R2007A/install_unix.sh 

```

gives
```

-------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        /media/MATHWORKS_R2007A/unix/update/install/main.sh: 168: /media/MATHWORKS_R2007A/unix/update/bin/glnxa64/xsetup: not found

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

    Sorry! Setup aborted . . .


```

but the file  /media/MATHWORKS_R2007A/unix/update/bin/glnxa64/xsetup is present in the dvd and is executable.

Any idea to install Matlab?
Thanks

---

### Post by TheLions on 2010-11-09
> **poiu said:**
> Hi,

I have exactly the same problem on Ubuntu 10.04. If I type the terminal version of the install this is what I get
```

sudo sh /media/MATHWORKS_R2007A/install_unix.sh -t
awk: linea progr.:2:    BEGIN { found = 0; extra = 9; min = 24; default = 24 }
awk: linea progr.:2:                                            ^ syntax error
awk: linea progr.:6:                if (nrows < min) nrows = default
awk: linea progr.:6:                                         ^ syntax error
awk: linea progr.:12:   END { if (found == 0) print (default - extra) }
awk: linea progr.:12:                                ^ syntax error
awk: linea progr.:12:   END { if (found == 0) print (default - extra) }
awk: linea progr.:12:                                                 ^ syntax error
awk: linea progr.:2: (FILENAME=- FNR=1) fatale: divisione per zero tentata in `%'
[: 582: -le: argument expected

```

while the command 
```

sudo sh /media/MATHWORKS_R2007A/install_unix.sh 

```

gives
```

-------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        /media/MATHWORKS_R2007A/unix/update/install/main.sh: 168: /media/MATHWORKS_R2007A/unix/update/bin/glnxa64/xsetup: not found

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

    Sorry! Setup aborted . . .


```

but the file  /media/MATHWORKS_R2007A/unix/update/bin/glnxa64/xsetup is present in the dvd and is executable.

Any idea to install Matlab?
Thanks

> If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

Try:
```
sudo sh /media/MATHWORKS_R2007A/install_unix.sh -t
```

---

### Post by poiu on 2010-11-15
Hi TheLions,

thank you for your reply. I already posted in the first line of my previous message what happens if I type the command you suggest: it doesn't seem to work

---

### Post by Wafaa on 2010-12-08
I had the exact same problem. It was a permission's problem. I solved it by copying the whole Matlab directory temporarily to my home folder. I then ran the following,

sudo chmod 777 -R /home/wafaa/matlab2009b

sudo /home/wafaa/matlab2009b/install

It worked and I was able to install matlab. Just delete the folder afterwards so it doesn't take up space. I couldn't figure out how to change permissions on a CD or an image of it.

---

