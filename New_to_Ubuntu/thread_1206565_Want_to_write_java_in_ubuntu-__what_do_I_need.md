---
title: "Want to write java in ubuntu-  what do I need?"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by kapi on 2009-07-07
Hi there, looking for some help regarding writing java (just learning) in ubuntu and wondered what I need to load (JRE  and SDK etc) for ubuntu.

Not too sure how to load a bin file so clear instructions wold be a great help please.

Thank you

---

### Post by taurus on 2009-07-07
Install it with either synaptic (System -> Administration -> Synaptic Package Manager) or apt-get.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-jdk
```
Or use Applications -> Add/Remove.

---

### Post by damis648 on 2009-07-07
Just do
```
sudo apt-get install sun-java6-jdk
```
and you should be good to go. If you want to start learning java, try BlueJ. It's a great ide to start off with. (The book they recommend is good too, I have it)

---

### Post by Boondoklife on 2009-07-07
I always like netbeans, its in the repositories. I think it will also install the JDK with it

---

### Post by rsiddharth on 2009-07-07
> **Boondoklife said:**
> I always like netbeans, its in the repositories. I think it will also install the JDK with it

Are you sure about this . I am also planning to install NetBeans 6.5 in my comp . If its really true then its then you don't need to install JDK 6 package separately !;) .

---

### Post by kapi on 2009-07-07
Thanks very much guys.

I have netbeans installed and as someone said bluej is good. I did java at college two years ago (using bluej) and have forgotten some of it.

So what you're saying is that I don't need to install the apt get as suggested. I can just use net beans because the libraries etc will be loaded when I installed netbeans. Or have I got it wrong?

---

### Post by Boondoklife on 2009-07-07
> **rsiddharth said:**
> Are you sure about this . I am also planning to install NetBeans 6.5 in my comp . If its really true then its then you don't need to install JDK 6 package separately !;) .

Well Im not able to try it out now, but I have used it before and do not recall having to install JDK afterwards. Besides you really would need the jdk to make any real use on the netbeans app so it would only make sence that it install it. Kinda link install a C ide without a C compiler. Give it a go, worst case scenario is you uninstall it or have to install the jdk anyway.

---

### Post by kapi on 2009-07-07
So is netbeans just a normal IDE used for java development or is it used for more specific purposes, Sorry if it sounds like a stupid question, I would just like to learn on the most appropriate application.

---

### Post by Boondoklife on 2009-07-07
> **kapi said:**
> So is netbeans just a normal IDE used for java development or is it used for more specific purposes, Sorry if it sounds like a stupid question, I would just like to learn on the most appropriate application.


Well there is no "Normal" when it comes to what you use to develop your code. I personally used vi to develop my first apps so vi was my normal. It is really just up to what you like and what app helps you out the most.

---

### Post by kapi on 2009-07-07
Thanks, for your patience Boondoklife

I guess I'll give netbeans ago. tried bluej at college and didn't like it. So I ended using a simple text editor. Geany is quite good too and as we speak I'm using Aptana for jquery tutorials, its not bad either.

---

### Post by rsiddharth on 2009-07-08
> **kapi said:**
> So is netbeans just a normal IDE used for java development or is it used for more specific purposes, Sorry if it sounds like a stupid question, I would just like to learn on the most appropriate application.
Here is a[ page]("http://www.netbeans.org/features/") which may help you know about Netbeans IDE . I use Netbeans in Windows Xp and is pretty cool - it auto completes your code and very good once you get the used to the IDE . 

 In Windows I installed the JDK6 separately and it didn't come with Netbeans . 

If you have installed Netbeans already and if your specifically looking at Java programming with the IDE   the[ link]("http://www.netbeans.org/kb/index.html") may  be of use .

---

### Post by Boondoklife on 2009-07-08
Ok got home and yea netbeans will install the jdk too so no need to do extra work.

---

### Post by rsiddharth on 2009-07-08
> **Boondoklife said:**
> Ok got home and yea netbeans will install the jdk too so no need to do extra work.
Thank you for saving me from extra work:KS

---

### Post by Boondoklife on 2009-07-08
Heh I should thank you, I have been putting off doing a project only cause i didnt have netbeans installed. Now I have no reason to bump it anymore!

---

