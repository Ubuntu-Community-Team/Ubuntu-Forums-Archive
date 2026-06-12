---
title: "Kaffeine momentarily playing dvds"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by bonez4ever on 2009-10-19
My Kaffeine player for Kubuntu 9.04 only plays dvd's for about a second or two then stops the dvd. I tried Dragon player too same problem and I also installed the lastest version of Kaffeine 0.8.7.The DVD I am also using works fine with Vista( it's Chronicles of Riddick just in case you wanted to know) If someone can help I would greatly appreciated it.

-Thanks
Bonez4ever

---

### Post by mgranet on 2009-10-19
Do you have kubuntu-restricted-extras installed?

---

### Post by bonez4ever on 2009-10-19
I don't know :confused: I installed a clean copy of Kubuntu just yesterday so unless it came with it I don't think I have it.

---

### Post by mgranet on 2009-10-19
Either search for kubuntu-restriced-extras in KPackageKit, and install it from there, or copy/paste the following into a terminal
```
sudo apt-get install kubuntu-restricted-extras
```

FYI - KPackageKit is under K-->Applications-->System-->Software Management (Kpackagekit)
You can also quick search for installed apps at the searchbox at the top of kickoff (the big blue K on your taskbar)

---

### Post by sandyd on 2009-10-19
> **mgranet said:**
> Either search for kubuntu-restriced-extras in KPackageKit, and install it from there, or copy/paste the following into a terminal
```
sudo apt-get install kubuntu-restricted-extras
```
 add
```

sudo apt-get install libdvdcss2 
```

---

### Post by mgranet on 2009-10-19
Good eye. I forgot restricted-extras only decodes unencrypted dvd's. I believe you need the medibuntu repos to get libdvdcss...

See here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by bonez4ever on 2009-10-19
Thank you but my Add or Remove programs disappeared after I attempted to install Kpackagekit. OI! how do I get it back?

---

### Post by mgranet on 2009-10-19
Umm...KPackageKit should already be installed. I think you UNinstalled it. :( The icons in PackageKit are a bit confusing. 

You can fix the problem by pasting into a terminal:
```
sudo apt-get install kpackagekit
```

Also, Add/Remove is really only for popular apps. If you want to install system type apps, or have access to the whole software repository, you have to use KPackageKit, or another package manager you install. (I suggest Synaptic)

---

### Post by bonez4ever on 2009-10-19
Um sudo command always does this to my system either that or your code isnt't working. [[IMG]http://img21.imageshack.us/img21/8199/snapshot6c.th.jpg[/IMG]]("http://img21.imageshack.us/i/snapshot6c.jpg/")

---

### Post by mgranet on 2009-10-19
That's not good.

Well, it's not my code. Your system appears messed up beyond my ability to help you. You should post a new thread about this, then re-try the steps we've posted here.

---

### Post by bonez4ever on 2009-10-19
But what about getting my add or remove programs back?:confused:

---

### Post by mgranet on 2009-10-19
You can't do that until you get the sudo problem fixed. :(

Once you get the sudo problem fixed, you can reinstall kpackagekit with ```
sudo apt-get install kpackagekit
```

EDIT: My bad for not explaining - Add/Remove disappeared because it uses kpackagekit as it's backend.

---

### Post by bonez4ever on 2009-10-19
> **mgranet said:**
> You can't do that until you get the sudo problem fixed. :(

Once you get the sudo problem fixed, you can reinstall kpackagekit with ```
sudo apt-get install kpackagekit
```
Oh:( well thank you  for the help.

---

### Post by mgranet on 2009-10-20
See my above edit, and you're welcome. :)

---

### Post by bonez4ever on 2009-10-20
> **mgranet said:**
> You can't do that until you get the sudo problem fixed. :(

Once you get the sudo problem fixed, you can reinstall kpackagekit with ```
sudo apt-get install kpackagekit
```EDIT: My bad for not explaining - Add/Remove disappeared because it uses kpackagekit as it's backend.
Cool so.. how do I get it back:KS

---

### Post by bonez4ever on 2009-10-20
Yea I made a post on helping me with my Terminal problem and I got it resolved all thanks to this wonderful community after that I installed everything and put all the codes I was told to, thanks again to the community for the codes. I then put Finding Nemo in my DVD and I got this [[img=http://img43.imageshack.us/img43/5369/snapshot7g.th.jpg] ]("http://img43.imageshack.us/i/snapshot7g.jpg/")
Oi!

---

### Post by mgranet on 2009-10-20
Did you check out the medibuntu link I posted earlier in this thread? Go there, read about it, then cut/paste in the code they provide. This will add the medibuntu repos to your update list. From there, you can install libdvdcss2. ```
sudo apt-get install libdvdcss2
```

---

### Post by bonez4ever on 2009-10-20
> **mgranet said:**
> Did you check out the medibuntu link I posted earlier in this thread? Go there, read about it, then cut/paste in the code they provide. This will add the medibuntu repos to your update list. From there, you can install libdvdcss2. ```
sudo apt-get install libdvdcss2
```
I' ll do it one more time.

---

### Post by bonez4ever on 2009-10-20
AWESOME IT WORKS!\\:D/ I love this community... I am in debt to everyone here that has helped me, thank you so much all you guys/girls rock :guitar:

P.S. Now it's time to watch Chronicles of Riddick and Finding Nemo

---

