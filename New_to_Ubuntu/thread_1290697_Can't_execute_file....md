---
title: "Can't execute file..."
date: 2009-10-13
forum: New to Ubuntu
---

### Post by tolinrome on 2009-10-13
Hi all,
After years of using Microsoft, I finally converted over to Ubuntu since Vista was corrupt on my laptop and I'm happy to start using opensource.

So, what I'm trying to do is execute a program I downloaded from Cisco - it worked on Vista, just unzipped it and executed it.

The directions for Ubuntu are:

**Linux:**
To install the Linux BIN packages, set the permission to be executable (chmod +x PacketTracer52_*.bin) then execute the binary in the terminal.

I read up on how to do this but couldnt find anything. Can someone please help me? Right now this all seems a little overwhelming to me, it's taking me a long time to do things that I'm so used to doing in Windows in seconds, but I WANT to learn Linux/Ubuntu so I'm determined to continue.

Thanks!

---

### Post by zerhacke on 2009-10-13
There's two ways to do this really.  There's the command line way and the GUI way.

The command line way is pretty easy, open a terminal under Applications -> Accessories.  Then just plug in the line you posted, the 

chmod +x PacketTracer52_*.bin

line, and press enter.

The GUI way, open Places -> Home, find the file, right click it, and select properties.  Go to permissions tab and check the execute button and hit OK.

Your choice which way to do it, really, but since you're going to need the command line to execute the file it would be easier to use the terminal for all of it.

---

### Post by jeremyswalker on 2009-10-13
Welcome to the community!

The process your instructions are referring to involves enter commands into a terminal. To open one, go to "Applications > Accessories > Terminal". Once the terminal is open, you can enter the commands specified. However, you need to ensure you are in the directory where the file is, or use the absolute path. For example, if it is on your desktop, use the following:
```
chmod +x /home/$USERNAME/Desktop/PacketTracer52_*.bin
```
You could then execute the file as follows:
```
/home/$USERNAME/Desktop/PacketTracer52_*.bin
```

---

### Post by tolinrome on 2009-10-13
Thanks Zerhacke,  I actually tried both ways you suggested before I wrote the post and it didn't work.
When I try the terminal way, after I press enter it just brings me to the prompt again waiting to type something - Example:
warren@ToshibaLaptop:~$ chmod +x PacketTracer52_*.bin
warren@ToshibaLaptop:~$

If I try through the GUI exactly as you suggested I get:
Could not display "/home/warren/PacketTracer52_i386_installer-deb.bin".
The file is of an unknown type.

The file is on my desktop and in the Home folder.

Thanks!

---

### Post by tolinrome on 2009-10-13
Hi Jeremyswalker,
I just saw your post. I'll try that. Thanks.

---

### Post by beastrace91 on 2009-10-13
Try running: ```
./PacketTracer52_*.bin
```

~Jeff

---

### Post by tolinrome on 2009-10-13
Hi Beastrace91,
Great! Looks like that did it. Thanks!!!
now.......where is the program? Cant find it anywhere. I saw that it unzipped it and I accepted the license agreement but it's hiding somewhere.
thanks everyone.

---

### Post by tolinrome on 2009-10-13
anyone???...

---

### Post by beastrace91 on 2009-10-13
It really truly depends on the program - read the documents that came with it. Most good apps will automatically add menu entries - but some do not.

~Jeff

---

