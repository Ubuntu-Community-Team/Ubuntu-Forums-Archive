---
title: "Linux=Open Source: how do i use this to my advantage?"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by abhigyan91 on 2009-07-04
hey every1,
as you can all probably tell, im new to ubuntu and linux:)

first of all, how can i use open source to my advantage?

i want to change certain programs, like the way they look, etc.. where do i find the files to which i can make changes to so that i can fiddle around with stuff like that?

for eg. i want to change the way g2ipmsg works.
I want to write a script to automatically adds all the ip addresses in my campus say 10.1.1.xx where xx ranges from 10-50.. i need to find the actual file of the program.. plz help me out..thx in advance

i checked /usr/bin and found the g2ipmsg file but i cant open it in any of the text editors(gedit etc).. nor does it work when i use 'cat' or vim in the shell.. dunno what to do.
i dont think there is a problem with the file permissions because i am able to open and read it its just that all i c is a bunch of gibberish..in fact when i stop it with cntrl+Z the whole terminal begins to act weird and returns stuff in a font i cant understand at all..

```

ls -l /usr/bin/g2ipmsg

```
this returns
> 
-rwxr-xr-x 1 root root 449060 2007-11-13 09:53 /usr/bin/g2ipmsg


i have a feeling im not looking in the right place.

---

### Post by frunns on 2009-07-04
I'm not entirely on track with what you want to do, but yeah, you're looking in the wrong place. "bin" stands for binary, so you you're trying to read a binary file, which isn't meant to be read by humans... I'd suggest checking out the hidden files in your home folder.
```
ls ~/.*
```
And /etc usually contains some config files as well.

---

### Post by abhigyan91 on 2009-07-04
hmm ok.. i checked the .g2ipmsg files in my home folder..nothing only the RSA encryption public and private keys.. tho i dnt know wht u need encryption for in a simple messenger system.. any other ideas anyone?

---

### Post by CatKiller on 2009-07-04
> **abhigyan91 said:**
> first of all, how can i use open source to my advantage?

If you want to change the source, first you need to acquire it. It isn't generally included; you would normally have the programs installed in binary form where it had already been compiled to run on a computer as opposed to being read by a human. Then, having acquired the source code (using apt-get source or whatever CVS system the project in question uses) and changed it to your satisfaction, you would compile your modified source using one of the compilers that are available (build-essential is a package that has most things that you'll need to compile your own programs).

For simple re-confonfiguration you probably just need to read the program's documentation.

---

### Post by Tibuda on 2009-07-04
To download the source code of any package, you can run this command:
```
apt-get source packagename
```
(no, you don't need sudo)

It will download the package source code to the current folder, and then you'll be able to start working with it.

---

### Post by servicetech on 2009-07-04
This is 'absolute beginner' stuff?
I must be WAY behind on my Linux knowledge...

---

### Post by abhigyan91 on 2009-07-04
hmm ok thx alot guys.. will try it out when i get back to my laptop and post back..
catkiller..how do i know if i have build-essential installed?

also i ran apt-get source g2ipmsg and it gave this:

> 
abhigyan@abhigyan-laptop:~$ cd Desktop/
abhigyan@abhigyan-laptop:~/Desktop$ apt-get source g2ipmsg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for g2ipmsg
abhigyan@abhigyan-laptop:~/Desktop$ 


seems its not there in the repos.. any ideas on how to get it?

also, is the source code normally just a text file(like most other things in linux)?coz if it is then what does build essential do?

---

### Post by abhigyan91 on 2009-07-04
ok jus to see what source code looks like i got the source code for gedit the text editor:
wow.. its overwhelming.. ne1 have ne idea how to decipher this stuff?
plz guide me to a tutorial to get me started on stuff like this.

Thanks:P

---

### Post by Celauran on 2009-07-04
> **abhigyan91 said:**
> ok jus to see what source code looks like i got the source code for gedit the text editor:
wow.. its overwhelming.. ne1 have ne idea how to decipher this stuff?
plz guide me to a tutorial to get me started on stuff like this.

Thanks:P

gedit is written in C. There are innumerable tutorials on C programming available online. It's not something you pick up overnight, though.

I keep going back to this:

> **abhigyan91 said:**
> 
I want to write a script to automatically adds all the ip addresses in my campus say 10.1.1.xx where xx ranges from 10-50.. i need to find the actual file of the program.. plz help me out..thx in advance


and can't help but feel modifying existing source is overkill. What is it exactly you're trying to do? It's likely much easier to just create a script for the specific task you're looking to accomplish.

---

### Post by abhigyan91 on 2009-07-04
> **Celauran said:**
> 
I keep going back to this:



and can't help but feel modifying existing source is overkill. What is it exactly you're trying to do? It's likely much easier to just create a script for the specific task you're looking to accomplish.

g2ipmsg is a sort of instant messenger which works on a local network. In my college, i have an intralan thing throughout the campus where each terminal(i.e hostel room) has an static ip allocation ranging in format 10.xx.xx.xxx, eg 10.3.3.86

now normally the program should automatically detect other people using this program but, it only picks up the people if they are on the same subnet. i.e if my ip is 10.3.3.86, then my g2ipmsg only picks up people with ip of the format 10.3.3.xx(xx varies from 1-255 as usual).

thus to 'see' people from other subnets, i have to manually add the ip address, eg if i want to 'see' say 10.4.4.86, i have to add it to the option in pref. i want to automate this process and add all possible ips that are possible. 

i know that i have to add the following ips:
10.3.1.xx
10.3.2.xx
..
..
10.3.16.xx

and 

10.4.1.xx
10.4.2.xx
..
..
10.4.15.xx

is there any way to do that?

---

### Post by Tibuda on 2009-07-04
> **abhigyan91 said:**
> seems its not there in the repos.. any ideas on how to get it?
How have you installed it? If it is not in repositories, you should look in the application web page for a source code archive. Linux is opensource, but remember it can run closed-source applications.

> **abhigyan91 said:**
> ok jus to see what source code looks like i got the source code for gedit the text editor:
wow.. its overwhelming.. ne1 have ne idea how to decipher this stuff?
plz guide me to a tutorial to get me started on stuff like this.

Thanks:P
It depends on the programming language used to develop that application. It's like learning a language.

---

### Post by synapsys on 2009-07-04
Sounds like you could do this relatively easily with a bash script. Sorry, you're going to have to learn that too...

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by Celauran on 2009-07-04
> **abhigyan91 said:**
> 
i know that i have to add the following ips:
10.3.1.xx
10.3.2.xx
..
..
10.3.16.xx

and 

10.4.1.xx
10.4.2.xx
..
..
10.4.15.xx

is there any way to do that?

In python,
```

to_write = ""
for i in range(3,5):
    for j in range(1,17):
        for k in range(1,256):
            to_write += "10." + str(i) + "." + str(j) + "." + str(k) + "\n"
of = open('output', 'w')
of.write(to_write)
of.close()

```

This will write the whole list to a file called output. That more or less what you need?

---

### Post by durand on 2009-07-04
If you can find the config file it uses, you can use a bash script to add the ip addresses to the file. It would just be a very simple loop.

---

### Post by abhigyan91 on 2009-07-04
yes that is exactly what i need, but how do i automatically add it to g2ipmsg,
i dont want to do it manually,that's the main point
the python code above gives a file that contains all the possible ips. now what shud i do to this file?

---

### Post by Celauran on 2009-07-04
> **abhigyan91 said:**
> yes that is exactly what i need, but how do i automatically add it to g2ipmsg,
i dont want to do it manually,that's the main point
the python code above gives a file that contains all the possible ips. now what shud i do to this file?

Copy/paste into g2ipmsg's config file?

---

### Post by abhigyan91 on 2009-07-04
exactly, i dont know where to find that config file:(

---

### Post by durand on 2009-07-04
Use the search tool to find it? Or read the manual for that program.
```
man g2ipmsg
``` might work.

---

### Post by abhigyan91 on 2009-07-04
tried it doesnt give anything

> abhigyan@abhigyan-laptop:~$ man g2ipmsg
No manual entry for g2ipmsg
See 'man 7 undocumented' for help when manual pages are not available.
abhigyan@abhigyan-laptop:~$ 


---

### Post by durand on 2009-07-04
Well, it clearly has a config because its saving those ip addresses somewhere. Are you sure there is no file or folder in you home called something like that with the settings? In the file manager, press Ctrl + H to view hidden files.

---

### Post by abhigyan91 on 2009-07-04
> **durand said:**
> Well, it clearly has a config because its saving those ip addresses somewhere. Are you sure there is no file or folder in you home called something like that with the settings? In the file manager, press Ctrl + H to view hidden files.
yes i checked the .g2ipmsg folder and it doesnt give anything substantial:

```

ls -l ~/.g2ipmsg
```

> 
abhigyan@abhigyan-laptop:~$ ls -l /home/abhigyan/.g2ipmsg/
total 24
-rw------- 1 abhigyan abhigyan  887 2009-07-04 12:42 priv-key-1024
-rw------- 1 abhigyan abhigyan 1675 2009-07-04 12:42 priv-key-2048
-rw------- 1 abhigyan abhigyan  497 2009-07-04 12:42 priv-key-512
-rw------- 1 abhigyan abhigyan  251 2009-07-04 12:42 pub-key-1024
-rw------- 1 abhigyan abhigyan  426 2009-07-04 12:42 pub-key-2048
-rw------- 1 abhigyan abhigyan  162 2009-07-04 12:42 pub-key-512


no config file, these just contain encryption keys (RSA encryption public and private keys)..
no list of ips
wait a minute.. it says total 24... what does that indicate? 24 files? the command only returns 6 files..:O wt is happening?

---

### Post by durand on 2009-07-04
Maybe in .config? Maybe it's in gconf rather than a file?
```
gconf-editor
```

---

### Post by abhigyan91 on 2009-07-04
> **durand said:**
> Maybe in .config? Maybe it's in gconf rather than a file?
```
gconf-editor
```


i think we're getting warmer:
the list of ips is stored in broadcasts, it says this is in /apps/g2ipmsg/broadcasts (as you can see from the bottom attachment where it says key name) but the thing is no such file exists in my file system!!
/apps==?? no such dir!

---

### Post by durand on 2009-07-04
Gconf is similar to the windows registry, it has a flat file database of xml files located in ~/.gconf but that is not how you edit it.

Since Celauran has already written a perfectly good python script, you can just edit it to do the job for you. Normally, you would use gconf's python bindings but here you can just copy and paste the output into the gconf editor. I've edited the script so that you can do that below.

```

to_write = ""
for i in range(3,5):
    for j in range(1,17):
        for k in range(1,256):
            to_write += "10." + str(i) + "." + str(j) + "." + str(k) + ","
print "[%s]"%to_write[:-1]

```

EDIT: Just double click on the field in gconf and copy and paste the output of the script there.

---

### Post by durand on 2009-07-04
Now that I've seen the output, I'm not sure how well it would work. You may need a more complex script to actually work out which ip addresses you want because the script generates 17*256*3 = 13056 ip addresses. Adding this to gconf will probably slow down gnome by a lot. Gconf may even have a field size limit. I'm not sure how your intranet works, but you could go through each ip address and ping each one to check whether it exists or not and only then add it because I highly doubt your network has 13056 networked computers...

---

### Post by Celauran on 2009-07-04
Might be worth checking if it supports wildcards or ranges. CIDR would be ideal here.

---

### Post by abhigyan91 on 2009-07-04
hmmm yea python worked well, but i c your point, its not accepting all that information. true we only have about 2500 or so, so i guess ill have to figure out something  out along those lines.(am not in campus rite now.. vacations :P) thanks alot durand and celauran.

---

### Post by Linux000 on 2009-07-04
Wouldn't that python script bring up 10.3.1.256 as an IP? If it does when its output is in the program, it will try to ping 10.3.1.256, which is an IP that doesn't exsist, IP's go from 0-255.

---

### Post by durand on 2009-07-04
Nope, I was wrong about my maths.
```

>>> range(0,5)
[0, 1, 2, 3, 4]

```

range() doesn't count the last number.

---

### Post by Linux000 on 2009-07-04
Okay, thanks for clearing that up.

---

### Post by Old_Grey_Wolf on 2009-07-04
> **abhigyan91 said:**
> 
i know that i have to add the following ips:
10.3.1.xx
10.3.2.xx
..
..
10.3.16.xx

and 

10.4.1.xx
10.4.2.xx
..
..
10.4.15.xx

is there any way to do that?

Have you tried entering 10.3.0.0/24 or 10.4.0.0/24?

---

### Post by abhigyan91 on 2009-07-06
nope, it doesn't help..tho i didnt kno u could enter that.. can you explain the slashes?

---

