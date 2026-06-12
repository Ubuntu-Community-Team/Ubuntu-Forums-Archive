---
title: "uninstall verilog"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by themis on 2009-04-30
Hello to you all, 

I would like to make a really stupid question

I have installed the verilog package provided by this link
  [ftp://ftp.icarus.com/pub/eda/verilog/v0.8/](ftp://ftp.icarus.com/pub/eda/verilog/v0.8/)

but I have installed in the wrong place.(desktop)
How can I uninstall it? Or move it somehow.

I used these commands

tar xvfz verilog&#8208;0.8.7.tar.gz 
cd verilog&#8208;0.8.7 
./configure 
make 
make install 


Thank you !!! :)

---

### Post by Zeedok on 2009-04-30
What happens when you try to move it - ie do you get some error message about permissions?

If you need to delete a file but don't have permissions you can do one of two things:

1. Command line:
- use the "cd" command to get to the directory that the file is in, eg
```

zeedok@zeedok-laptop:~$ cd /home/zeedok/Desktop
zeedok@zeedok-laptop:~/Desktop$ 
```

then delete the file you don't want with "rm"

2. Run nautilus as a sudo:

At the terminal run:

```
sudo nautilus
```

Then just delete away (carefully!!)

Once there

---

### Post by themis on 2009-05-01
so when I delete the file verilog will not be installed ?

then I can repeat the install process without any problems?

Thanks again.
I haven't removed anything yet

---

