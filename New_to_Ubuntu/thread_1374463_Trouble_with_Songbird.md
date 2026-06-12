---
title: "Trouble with Songbird"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by myolbug on 2010-01-06
I am trying to follow these directions, but I must be missing something.  I have extracted the file to desktop, but I cannot figure out the code necessary.

Can someone please give me the ID10T guide please?

[http://www.jonathanmoeller.com/screed/?p=1228](http://www.jonathanmoeller.com/screed/?p=1228)

---

### Post by ThePinkWitch on 2010-01-06
make that two copies I'm having a nightmare with getting Ububtu set up LOL :)

---

### Post by jmszr on 2010-01-06
mylobug,

You can install Songbird from GetDeb: [http://www.getdeb.net/software/Songbird](http://www.getdeb.net/software/Songbird) - unless your heart is set on compiling it.

---

### Post by LuisGMarine on 2010-01-06
or follow the guide in my signature to have the latest one =), .debs work just as well ...

---

### Post by myolbug on 2010-01-07
I have tried both but it still won't work.  

jmszr, I get a message that says it can't find Songbird. 

LuisGMarine I get the following, even after following your directions:

tar: Songbird*.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors


Options?

---

### Post by llawwehttam on 2010-01-07
All i can say is [https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

hope it helps.

---

### Post by LuisGMarine on 2010-01-07
> **myolbug said:**
> I have tried both but it still won't work.  

jmszr, I get a message that says it can't find Songbird. 

LuisGMarine I get the following, even after following your directions:

tar: Songbird*.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors


Options?

Those errors are saying your are not in the right directory.  In other words you are running this command in a folder where you **DID NOT** download the songbird tar.gz.

When you save it, make not of it and cd into that directory.  For example if you downloaded it to your /home/user_name/Desktop, make sure you cd in that directory by typing in

```
cd /home/user_name/Desktop
```

the 
```
sudo tar -xvzf Songbird*.tar.gz -C /opt/
```

has to be ran in the same directory where the songbird tar.gz resides.

---

### Post by myolbug on 2010-01-07
Should I save it to my desktop or extract it there?

---

### Post by LuisGMarine on 2010-01-07
save it to your Desktop. When you open up your terminal window Change Directory into your Desktop by running the following command.

```
cd /home/user_name/Desktop
```

of course substitute "user_name" with your actual user name.

---

### Post by myolbug on 2010-01-07
Thanks, that was the part missing from your directions.  Perhaps you can add them in, so noobs like me can get them?
Regardless, it is working now, so thank you!

---

