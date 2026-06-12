---
title: "LiveCD Wireless (BCM4603) Troubleshoot (missing bcm43xx executable)"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by maclenin on 2006-12-20
A quick (and reconfigured) excerpt from a larger post ([http://ubuntuforums.org/showthread.php?t=319939)](http://ubuntuforums.org/showthread.php?t=319939)) re: activating my wireless card (BCM4306) while running Edgy Eft via LiveCD on a Dell Inspiron 600m (without a connection to the internet)....

A. I am trying to unpack bcm43xx-fwcutter-006.tar.bz2 ("tool") so I can use it to cut firmware from bcmwl5.sys ("driver"). I have downloaded the tool (in Windows XP via [http://developer.berlios.de/project/...?group_id=4547](http://developer.berlios.de/project/...?group_id=4547)) into a windows partition and copied it over to a Linux partition:

```
sudo cp /c/windows/linux/bcm43xx-fwcutter-006.tar.bz2 /home/utilities
```

B. I have tried unpacking the tool using the following... 

```
ubuntu@ubuntu:/home/utilities$ sudo tar -jxvf bcm43xx-fwcutter-006.tar.bz2 -C /home/utilities
```

...with apparent success...

```
bcm43xx-fwcutter-006/
bcm43xx-fwcutter-006/bcm43xx-fwcutter.1
bcm43xx-fwcutter-006/Makefile
bcm43xx-fwcutter-006/md5.c
bcm43xx-fwcutter-006/README
bcm43xx-fwcutter-006/fwcutter_list.h
bcm43xx-fwcutter-006/fwcutter.c
bcm43xx-fwcutter-006/fwcutter.h
bcm43xx-fwcutter-006/COPYING

ubuntu@ubuntu:/home/utilities$
```

...however, I cannot find the executable. Repeated unpacking efforts have lead to the same result.

Any thoughts?

My ultimate goal, of course, is to unpack the tool, find the executable and cut the firmware from the driver (which has also been copied from a windows partition to the Linux partiton: /home/drivers).

---

### Post by maclenin on 2006-12-25
As I Googled around, trying to resolve the missing executable issue, I think I learned that I had been unpacking the tool correctly, however, I also found that I still needed to recompile the unpacked tool in order to "make" the executable ([http://www.root-forum.org/system-installieren/2414-suse-upgrade-von-10-1-auf-10-2-a-3.html](http://www.root-forum.org/system-installieren/2414-suse-upgrade-von-10-1-auf-10-2-a-3.html)). 

Therefore, I've tried the following:

```
cd /directory/into_which/the_tool/has_been_unpacked
```

...and then, from that directory...

```
make
```

...to recompile the tool (and generate the executable).

Here is a very brief summary of the (huge) list of errors I received as I ran the "make" command:

```
fwcutter_list.h:1653: error: unknown field 'iv_pos' specified in initializer
fwcutter_list.h:1653: warning: excess elements in struct initializer
fwcutter_list.h:1653: warning: (near initialization for 'files[124]')
fwcutter_list.h:1654: error: unknown field 'iv_map' specified in initializer
fwcutter_list.h:1654: warning: excess elements in struct initializer
fwcutter_list.h:1654: warning: (near initialization for 'files[124]')
```

...as well as:

```
fwcutter.c: In function 'do_cmp_arg':
fwcutter.c:655: error: 'size_t' undeclared (first use in this function)
fwcutter.c:655: error: expected ';' before 'arg_len'
fwcutter.c:659: error: 'arg_len' undeclared (first use in this function)
fwcutter.c:659: warning: incompatible implicit declaration of built-in function 'strlen'
```

...and, finally:

```
fwcutter.c:850: warning: implicit declaration of function 'extract_iv'
fwcutter.c:850: error: 'const struct file' has no member named 'flags'
fwcutter.c:851: error: 'const struct file' has no member named 'iv_pos'
fwcutter.c:852: error: 'const struct file' has no member named 'iv_map'
make: *** [fwcutter.o] Error 1
```

I am wondering how to resolve this wave of errors.

Might there be a problem with the files I'm trying to recompile?

Is there something I need to be doing differently?

Thanks for any suggestions.

---

### Post by maclenin on 2006-12-29
As Googling continued I came across a helpful (hopeful) reference to running "./configure && make" in the following post ([http://hangdog.pihl.no-ip.org/index.php?option=com_content&task=view&id=14&Itemid=34](http://hangdog.pihl.no-ip.org/index.php?option=com_content&task=view&id=14&Itemid=34)) and eagerly proceeded to reload the LiveCD and remount / recopy / and retar respective directories and files using this general sequence of commands, in anticipation of finally having solved the wireless riddle:

A. At first, all's well - 

```
sudo mkdir /c
sudo mount /dev/dha2 /c -t ntfs
sudo mkdir /home/utilities
sudo mkdir /home/drivers
sudo cp /c/windows/linux/bcm43xx-fwcutter-006.tar.bz2 /home/utilities
sudo cp /c/windows/system32/drivers/bcmwl5.sys /home/drivers
cd /home/utilities
sudo tar -jxvf bcm43xx-fwcutter-006.tar.bz2 -C /home/utilities

bcm43xx-fwcutter-006/
bcm43xx-fwcutter-006/bcm43xx-fwcutter.1
bcm43xx-fwcutter-006/Makefile
bcm43xx-fwcutter-006/md5.c
bcm43xx-fwcutter-006/README
bcm43xx-fwcutter-006/fwcutter_list.h
bcm43xx-fwcutter-006/fwcutter.c
bcm43xx-fwcutter-006/fwcutter.h
bcm43xx-fwcutter-006/COPYING

ubuntu@ubuntu:/home/utilities$
```

B. And then the fun begins - 

1. With reference to the link, above (among others), it seemed that I now had to change directories to that within which the unpacked tool's files reside...

```
cd /home/utilities/bcm43xx-fwcutter-006
```

2. ...in order to compile them...

```
./configure
```

3. ...to create the Makefile - in prep. for the make command...

```
make
```

4. ...which would then generate the executable that I would use to cut the firmware from the driver.

```
fwcutter /home/drivers/bcmwl5.sys
```

5. Then, I would change the directory to that within which the freshly cut .fw (firmware) files reside...

```
cd /home/drivers
```

6. ...to run the following...

```
sudo make installfw
```

...to make certain the .fw was installed into it's proper directory (/lib/firmware).

C. However - 

re: 2. I could not use the ./compile command. Perhaps because the tool's Makefile already existed? Every time I tried to use the command, I would receive the following error:

```
bash: ./configure: No such file or directory 
```


re: 3. I ran the make command - after the ./configure failed - and received the multiple pages of errors, which I've already summarized in the previous post.

I can unpack fwcutter, I just can't find / generate the fwcutter executable!

Any tiniest bits of advice would be welcomed.

---

### Post by maclenin on 2007-01-15
This is where I ended up...

[http://ubuntuforums.org/showthread.php?t=332253](http://ubuntuforums.org/showthread.php?t=332253)

...and am currently in wireless connectivity trouble-shoot mode:

[http://ubuntuforums.org/showthread.php?t=331997](http://ubuntuforums.org/showthread.php?t=331997)

I chose bcm43xx because it seemed cleaner than ndiswrapper - but am not opposed to wrapping (or another solution) should all else fail....

---

### Post by maclenin on 2007-01-31
The [**latest**]("http://ubuntuforums.org/showthread.php?t=340689")....

---

