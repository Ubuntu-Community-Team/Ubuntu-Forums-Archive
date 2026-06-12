---
title: "how to mount uif"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by powel212 on 2009-02-28
Anybody know how to mount .uif CD image in Ubuntu or convert .uif to .iso ?

i know this works for iso
sudo mount filename.iso /media/cdrom0 -o loop
hoping there is some way to do the same thing with uif

Thanks

Powel

---

### Post by taurus on 2009-02-28
You can use uif2iso to convert it to .iso and use the command in your OP to mount it.

[http://linux.softpedia.com/get/Utilities/UIF2ISO-35316.shtml](http://linux.softpedia.com/get/Utilities/UIF2ISO-35316.shtml)

---

### Post by powel212 on 2009-02-28
Thanks to you and to Luigi for making this little dos based program. Works the charm. 

I was hoping for a native linux app that could do the same thing if anyone knows.

Thanks

powel

---

### Post by doktor_apokalypse on 2009-02-28
I know it's not really linux native, but I just used it like this abbout five minutes ago: ```

sirius@dogstar:~$ wine uif2iso.exe <filename>.uif <filename>

```

and it did everything right there in the terminal, no problem, no fake wine windows window.  Of course that means you have to have wine, but hey...  I don't think anybody else has broken the encryption on uif and made a tool for it.

---

### Post by powel212 on 2009-02-28
If that is as close as I can get, that is certainly a nice alternative. Thank you for:

wine uif2iso.exe <filename>.uif <filename>

I have wine installed but never use it. But this sounds like a great opportunity give it a try.

Thanks again

Powel

---

### Post by gonkyouka on 2009-05-12
ive tried this code:
```
sirius@dogstar:~$ wine uif2iso.exe <filename>.uif <filename>
```

but it gives me this error:

```
wine: could not load L"C:\\windows\\system32\\uif2iso.exe": Module not found

```

I have wine installed...

---

### Post by statmonkey on 2009-08-22
You don't need to run wine to accomplish this if you don't want to.  

> sudo apt-get install zlib1g zlib1g-dev libssl-dev build-essential

Gives you Zlib and openssl

Download uif2iso written by Luigi Auriemma.
 
> sudo wget [http://aluigi.altervista.org/mytoolz/uif2iso.zip](http://aluigi.altervista.org/mytoolz/uif2iso.zip)

Go to the directory you downloaded uif2iso.zip to and type:

> unzip uif2iso.zip

and then

> cd src

Now to pull it together type (in the src directory)

> make

and then  

> sudo make install

Convert to iso by going to the directory your uif is in and typing:

> uif2iso your.uif yournew.iso

I would recommend mounting it with gmount-iso which you can get by typing:

> sudo apt-get install gmountiso

gmount-iso will show up in System Tools in your menu.  Before mounting you will need to create a mount point.  I would suggest in your /media directory. Like:

> sudo mkdir /media/mynewiso

You can also mount by command line but I am lazy and like the ease that gmountiso gives me.

I found these instructions at [http://wesleybailey.com/articles/convert-uif-to-iso]("http://wesleybailey.com/articles/convert-uif-to-iso") and reproduce them here just to save someone from the hunting I went through.  I find this method by far the easiest I have ever found.  Good luck.

---

### Post by LinuxHelper on 2010-08-26
Statmonkey....

I appreciate the help but the final link you pointed out, but it does not work for me.

I searched that guys site and found the need like that shows how to install uif2iso in linux. I read through the comments and found out how to fix the [uif2iso wrong bbis signature    ]("http://wesleybailey.com/articles/uif-to-iso-converter")

---

### Post by cas118 on 2011-03-19
Just an update for those looking at this topic.

Ubuntu 10.10 has a native uif2iso tool:

```
sudo apt-get install uif2iso
```

Job done :)

---

