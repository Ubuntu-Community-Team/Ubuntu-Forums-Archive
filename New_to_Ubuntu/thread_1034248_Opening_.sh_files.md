---
title: "Opening .sh files"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2009-01-08
I recently downloaded a program with a setup.sh file and tried to open it in terminal but despite following the instructions for opening this file I still get the 
" can't open setup.sh " message. I tried downloading the alternative tar.gaz file but got lost trying to understand tarballs.

---

### Post by cdtech on 2009-01-08
The .sh is a shell script. You can run the script within a terminal using:
```
./setup.sh
```
To edit the script you would have to use an editor:
```
pico setup.sh
```

---

### Post by tombott on 2009-01-08
Ok download setup.sh
Open the Terminal, change to the directory you downloaded the file too, for example

```
cd home/userid/desktop 
```

Then execute the script with the following command:
```
sh setup.sh
```

Let us know if that works.

---

### Post by ex-wirecutter on 2009-01-08
Thanks for the reply , but thats exactly what I tried with the exception of putting " sudo " first. I still get " can't open " message .
Have also tried a fresh download but just the same . Why do they have to have so many different ways of writing setup files , I dont have any trouble with .deb installations .

---

### Post by tombott on 2009-01-08
> **ex-wirecutter said:**
> Thanks for the reply , but thats exactly what I tried with the exception of putting " sudo " first. I still get " can't open " message .
Have also tried a fresh download but just the same . Why do they have to have so many different ways of writing setup files , I dont have any trouble with .deb installations .

hmm, whats the link for the setup.sh file, might be worth me trying it as well.

Just out of interest try doing this:

Open the terminal and type:
```

wget http://freetowatchtv.co.uk/images/ubuntu/install.sh
sh install.sh
```

Does that work for you?

---

### Post by hyper_ch on 2009-01-08
> **tombott said:**
> Then execute the script with the following command:
```
sh setup.sh
```

This works if the file is executable - which a plain downloaded file shouldn't be.

---

### Post by tombott on 2009-01-08
> **hyper_ch said:**
> This works if the file is executable - which a plain downloaded file shouldn't be.

Erm really?
Always works for me after downloading via wget or Firefox.

---

### Post by ex-wirecutter on 2009-01-08
Just got the " unable to resolve " error , never mind I will just have to abandon the program and stick to .deb packages . Thanks anyway .

---

### Post by joshmuffin on 2009-01-08
Is it exacutable?
In nautilus: right-click -> properties -> permissions -> tick  'Allow executing as a program'

---

### Post by ex-wirecutter on 2009-01-08
Thanks again for all your suggestions , but this is all getting too complicated for me as I am new to Ubuntu . Think I will just give this one a miss . Much obliged.

---

### Post by lazyart on 2009-01-08
That's a shame.  From a security standpoint it makes a lot of sense... you can't simply download a shell script and have it run without some intervention.

From the shell you can```
chmod +x filename
```

I'd suggest you learn these things-- it is common practice in linux.

---

### Post by lazyart on 2009-01-08
dbl post

---

