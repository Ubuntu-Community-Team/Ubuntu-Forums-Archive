---
title: "Downloaded Frostwire no"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-02-23
Icon came up, and I can't find it, so I downloaded it again and it says already installed, which is what I wanted, but I can't find it.
While I'm here Rythmbox has graciously installed over 800 songs that will, unfortunately, never see the light of day around here.  I've just started looking at it but how do I DELETE almost all of them?  Gateway laptop 6436, Gig & 1/2 RAM.
Thanks

---

### Post by taurus on 2009-02-23
I assume you installed it from the repos.  Do you see an icon in Applications -> Internet?  Otherwise, try typing in the name of it from a terminal and see what happens.

Applications -> Accessories -> Terminal
```
frostwire
```
p.s.  Make sure you have install Sun's java on your machine first since frostwire will look for it.

---

### Post by Yed Ied on 2009-02-23
No, I can't find it, but I did find "sudo apt-get install sun-java6-jre". Ran that in Terminal, did restart, back to Terminal and ran "frostwire" and it said it couldn't find java.
As far as Rythembox, I figured that out.
Thanks

---

### Post by llamabr on 2009-02-23
Try:

which frostwire

I don't see it in my repos.  how did you install it?

---

### Post by yellowaeroplane on 2009-02-23
did you download the .deb, or did you build it from a tarball?

The .deb makes life a hell of a lot easier.

here's the link: [http://www.frostwire.com/download/?os=ubuntu&](http://www.frostwire.com/download/?os=ubuntu&)

Just install in with GDebi and it should magically appear in your Applications menu under "Internet"

8-)

---

### Post by taurus on 2009-02-23
> **Yed Ied said:**
> No, I can't find it, but I did find "sudo apt-get install sun-java6-jre". Ran that in Terminal, did restart, back to Terminal and ran "frostwire" and it said it couldn't find java.
As far as Rythembox, I figured that out.
Thanks

What's the output of this command for your java?

```
java -version
```

---

### Post by Yed Ied on 2009-02-23
I found Frostwire, right where you said it would be.  I put the icon in the tool bar.  I ran "java -version" in Terminal and got some info I didn't understand, but nothing that looked like the version.  I couldn't figure out how to copy & paste from Terminal,that wasn't available. It is in there though, frustating.

---

### Post by Yed Ied on 2009-02-23
Just an update, I found the Frostwire icon, but Frostwire can't find the Java application.

---

### Post by taurus on 2009-02-23
You highlight whatever text you want to copy with the left button and paste it here with the middle scroll ball.

---

### Post by Yed Ied on 2009-02-23
I'm on a laptop and I don't seem to be able to move the highlighted area, at all, is it my bad or just not working on a laptop?

---

### Post by Yed Ied on 2009-02-24
command prompt: java -verzion
The program java can be found in the followig programs.
*java-gcj-compat-headless
*cacao-oj6-jre-headless
*gij-4.2
*jamvn
*open jdk--6-jre-headless
*cacao
*gij-43
*sablevm
Try: sudo apt-get install <select package>
bash: java: command not found
steve@steve-laptop:~$
This is what I get in Terminal about Java & couldn't copy and paste.  Hope this makes sense, I typed it just as it was.
Thanks

---

### Post by taurus on 2009-02-24
Try reinstalling java again if you said you have before.

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
When you get to the licensing screen, press the Tab key to highlight the <OK> and Return to accept it.  Once it's all done, see if you have the right version of java as your default.

```
java -version
```

---

### Post by Paul41 on 2009-02-24
On a laptop pressing both the left and right mouse buttons at the same time will do the same thing as the middle button on a mouse.

---

