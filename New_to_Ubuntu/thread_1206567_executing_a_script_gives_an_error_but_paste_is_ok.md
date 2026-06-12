---
title: "executing a script gives an error but paste is ok"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by hardinej on 2009-07-07
Hi,
I have a question about shell scripting. I've run into this a couple of times, but I don't really understand what's happening. I write scripts in gedit and sometimes executing the script won't work but pasting will or vise versa. I really don't know what information would be useful to anyone who could help, but like I said, I use gedit and here is the beginning of my script and the error

#!/bin/sh
#
# Written by Jaro Hofierka, for v.surf.rst
# this is a script for a cross-validation analysis of RST parameters
# OUTPUT: CSV table
# Modified to do many cross-validations for different maps
#
# j - smoothing - the number after decimal point, e.g. sm=0.1 is defined as j = 10
# i - tension
dminOnes=( 1 1 1 2 3 )
dminDecim=( 04 12 38 12 06 )
for index in 0 1 2 3 4
do
  INMAP=JR_20080327
  OUTFILESTATS=/home/eric/Desktop/generalization/crossValidations/cv_2008_rst_"${dminOnes[index]}${dminDecim[index]}".csv
.....................
and the error is
./CV_2008_rst.sh: 10: Syntax error: "(" unexpected

I guess it thinks something is wrong with the array declaration, but only when I execute and not when I paste? This is really not a particularly urgent matter, I just think it's peculiar and since I'm still learning linux, bash, etc, I want to avoid work-arounds because understanding the problem usually teaches me something worthwhile.
Thanks,
Eric

---

### Post by sisco311 on 2009-07-07
In ubuntu /bin/sh is a symbolic link to /bin/dash.

The script works in bash.

[https://wiki.ubuntu.com/DashAsBinSh]("https://wiki.ubuntu.com/DashAsBinSh") 

[http://en.wikipedia.org/wiki/Debian_Almquist_shell]("http://en.wikipedia.org/wiki/Debian_Almquist_shell")

---

### Post by hardinej on 2009-07-07
Awesome!
Thanks

---

