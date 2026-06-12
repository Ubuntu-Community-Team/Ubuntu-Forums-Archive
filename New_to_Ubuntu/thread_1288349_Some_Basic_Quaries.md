---
title: "Some Basic Quaries"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by eeshan.mulye4 on 2009-10-11
i am a beginner to linux and kubuntu is my first system and first day after windows so i have some very basic questions

1.How to install blocked updates in kubuntu and why are they blocked
2.how to run a shell script(I have a am a problem with the doom 3 linux installer after i have given it chmod +ugo and chmod +x and ./ command
it has a problem)
3.How to enable 3d desktop effects of beryl and compiz.

---

### Post by MelDJ on 2009-10-11
1. what do you mean blocked? does an error come up?
3. beryl is no more! it has merged with compiz to make compiz fusion. download the compiz package from synaptic

---

### Post by eeshan.mulye4 on 2009-10-11
I forgot to mention my configuration 

1.Intel Core 2 Quad 2.4ghz
2.Nvidia Ge Force 8600 GT-512MB VRAM Dedecated And upto 2GB Shared
3.4 GB DDR 2 Ram
4.8 MB l2 Cache
5.500 GB SATA Hard Disk

Very Basic Configuration

---

### Post by eeshan.mulye4 on 2009-10-11
No Error Comes Up But A Red Cross Is There On The Blocked Updates.

---

### Post by MelDJ on 2009-10-11
and before you can use desktop effects. install it from hardware drivers

---

### Post by MelDJ on 2009-10-11
could you give a screenshot?

---

### Post by eeshan.mulye4 on 2009-10-11
There Are Three Kinds Of Updates Which Prop Up 
1.Big Fixes
2.Security Updates
3.Blocked Updates(which include some kind of kernel)

---

### Post by MelDJ on 2009-10-11
This happens when your update happens in the middle of a package 
update on your mirror. It is likely that the repository is being 
updated and some packages on which the **blocked** **updates** rely are not 
updated yet. 

And no, you don't have to force the update, just wait a few more hours 
(up to 2 days sometimes, depending on the speed of your mirror) to get 
the missing packages. 


Regards, Myriam.
  
i copied this from: [http://www.nabble.com/%28jaunty%29-What-are-blocked-updates--td23411820.html]("http://www.nabble.com/%28jaunty%29-What-are-blocked-updates--td23411820.html")

---

### Post by eeshan.mulye4 on 2009-10-11
Thank You Very Much For The Information

---

### Post by 3rdalbum on 2009-10-11
> **eeshan.mulye4 said:**
> 
2.how to run a shell script(I have a am a problem with the doom 3 linux installer after i have given it chmod +ugo and chmod +x and ./ command
it has a problem)

Running a shell-script installer involves two steps:

1. Making it executable by root
2. Running it in a terminal as root.

Why as root? Well, it's simple: Your normal user account can't modify any part of the system, only the contents of its home directory. This is for safety and security. If you want to modify anything outside your home directory, you need to modify it as root.

In a terminal, enter the following BUT DON'T PRESS ENTER YET.

```
sudo chmod a+x 
```

Press the space bar so there is a trailing space, and then drag the script to the terminal window. It will fill in the script's location, so now just click on the terminal window again to bring it to the foreground and press Enter.

You will be asked for your password; enter it and press Enter again.

Now just type "sudo", put a trailing space, and drag the shell script back onto the terminal and run the result.

Now the installer will run.

If there are any error messages, please reply to this thread again with the contents of the error message.

It's possible to make something executable by root without using the terminal, but it involves a lot more steps.

---

