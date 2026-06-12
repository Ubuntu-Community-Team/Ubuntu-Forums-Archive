---
title: "Setting environment variables on Ubuntu, a problem"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by gemm on 2009-09-22
Hi,

I cannot execute a command although I think I have set the PATH correctly.

In my /etc/profile file I have included at the end the following:

PATH=/home/my_software/MiniparSept2009/minipar-0.5-Linux32/pdemo:$PATH
export PATH

PATH=/home/my_software/Foma/linux/foma:$PATH
export PATH

I have restarted the computer and after typing echo $PATH, I get:

/home/my_software/Foma/linux/foma:/home/my_software/MiniparSept2009/minipar-0.5-Linux32/pdemo:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

I can now execute pdemo, however, I cannot execute foma.  

Previously, I have written in the /etc/profile file the following:

PATH=/home/my_software/MiniparSept2009/minipar-0.5-Linux32/pdemo:/home/my_software/Foma/linux/foma:$PATH
export PATH

but the result was the same (pdemo is executable, but foma not)

Do you know what is the problem, and what should I do?

Thanks for your help.

---

### Post by ohzopants on 2009-09-22
Is foma executable from that directory? (e.g. are you sure there isn't a bin/ directory in there somewhere)

---

### Post by gemm on 2009-09-22
> **ohzopants said:**
> Is foma executable from that directory? (e.g. are you sure there isn't a bin/ directory in there somewhere)

Hi! Yes, it is executable form everywhere when I specify the absolute path:

> /home/my_software/Foma/linux/foma

in whichever directory I am, when I specify the whole path it works. What I want is to make it possible to type just 

> foma

This works for the other program, pdemo: I can type both

>/home/my_software/MiniparSept2009/minipar-0.5-Linux32/pdemo
and
> pdemo

and it is executed (not matter from which directory).

In the beginning I had the same problem with pdemo as with foma. However, when I add the directory to the path as specified above it worked. It doesn't work for foma :(

And no, there is no bin directory, neither for pdemo, not for foma.

Thanks a lot in advance.

---

### Post by ohzopants on 2009-09-23
In your first post you indicated that you added /home/my_software/Foma/linux/foma.  That makes the directory foma under /home/my_software/Foma/linux/ part of your path.

You should try adding /home/my_software/Foma/linux to your $PATH, since that is the directory in which the executable your are trying to run is located in.

---

### Post by gemm on 2009-09-27
> **ohzopants said:**
> In your first post you indicated that you added /home/my_software/Foma/linux/foma.  That makes the directory foma under /home/my_software/Foma/linux/ part of your path.

You should try adding /home/my_software/Foma/linux to your $PATH, since that is the directory in which the executable your are trying to run is located in.

Thank you very much!!! Yes, it was the mistake, I have understood it now. thank you :)

---

