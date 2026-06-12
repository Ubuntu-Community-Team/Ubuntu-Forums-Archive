---
title: "Java aplet won't load, streaming stock qoutes"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by Committed on 2009-02-13
I loaded ubuntu on an old laptop I had.  IBM thinkpad, a22e, 800 mhz, 256m ram, 60g hardrive.  Everything's working fine, faster than xp but when I load my Scottrade account, I can't get my streaming qoutes and charts running.  I've enable Java and everything to do with it.  Popups enabled, although I don't believe they have to be.  Tried with both Firefox and Opera.

Here are screen shots of my main computer with all apps running and my laptop with the java aplet loaded but streaming qoutes not running.

[IMG][IMG]http://img.photobucket.com/albums/v298/Danceswithtrees/Dirtbiking/screenshot.jpg[/IMG][/IMG] 

Laptop w/ubuntu

[IMG][IMG]http://img.photobucket.com/albums/v298/Danceswithtrees/screenshotubuntu.jpg[/IMG][/IMG]

---

### Post by Committed on 2009-02-13
bump:confused:

This is the single most important thing I need this laptop for.  If it can't run my streaming qoutes, I'll have to dump ubuntu which I really don't want to do.  I like everthing else about it.

---

### Post by NetworkGuy on 2009-02-13
Assuming you installed the sun-java6 packages...  did you also install the sun-java6-plugin?  I believe that plugin is for FireFox to communicate to the JRE.

---

### Post by avtolle on 2009-02-13
You've enabled Java; which one (Sun or the open-source one)?

---

### Post by RVA Dennis on 2009-02-13
I had a similar problem with streaming quoters but in my case I was able to get a JavaWS app to run but horrible rendering.

Have not yet gotten around to trying Scot Trade but will attempt it this weekend and if successful I'll report back with my work around.

---

### Post by Committed on 2009-02-13
> **avtolle said:**
> You've enabled Java; which one (Sun or the open-source one)?

Sun.  Checking on sun-java6-plugin now.

---

### Post by Committed on 2009-02-13
Well, I guess I don't have it installed.  I just enabled it on my browsers.  Have to do some more checking.  Going to Suns site unless someones got a link on what to download.  First day with ubuntu.

---

### Post by NetworkGuy on 2009-02-13
Did you install the sun-java6-plugin?

---

### Post by Committed on 2009-02-13
> **NetworkGuy said:**
> Did you install the sun-java6-plugin?

No. Looking for it now.

---

### Post by NetworkGuy on 2009-02-13
```
sudo apt-get install sun-java6-plugin
```

You can install the entire java package from either apt-get or synaptic

---

### Post by Committed on 2009-02-13
> **NetworkGuy said:**
> ```
sudo apt-get install sun-java6-plugin
```

You can install the entire java package from either apt-get or synaptic

Sorry man, I am a total new to linux.  I don't have a clue where to type code into.

---

### Post by NetworkGuy on 2009-02-13
Not a problem.  

Accessories -> Terminal

I recommend you also check out  System -> Administration -> Synamptic package mananger.


You will be surprised just how many ready to install packages are there.   No compiling or researching what you need.   Like the old Prego spaghetti sauce commercials.  "It's in there"

---

### Post by Committed on 2009-02-13
Found Java Package in there.

---

### Post by NetworkGuy on 2009-02-13
Ok, now is the box next to Java6-plugin greyed?   If it is, then the plugin is installed.

---

### Post by Committed on 2009-02-13
That didn't work.  Typed in under app/acc/terminal: sudo apt-get install sun-java6-plugin

says: couldn't find package sun-java6-plugin

---

### Post by NetworkGuy on 2009-02-13
Try this 

```
 sudo apt-get update 
```

This will make sure that your machine downloads all the header files about all the packages available.

Then try to install the plugin again.

---

### Post by Committed on 2009-02-13
Doing that right now.  Found online how to install.  It's loading right now.  Will know in a minute. looks good so far.

---

### Post by Committed on 2009-02-13
Ok, I'm at Configuring sun-java6-jre

SUN MICRO SYSTEMS IS WILLING TO LICENCE THE HAVE PLATFORM STANDARD ADDITION DEVELOP KIT TO YOU ONLY UPON..........ACCEPTING TERMS..........

                    <OK>

How the heck do I accept it?  There is nothing to click or accept.

---

### Post by NetworkGuy on 2009-02-13
Tab??   Enter Key?

I would honestly just do the installs from Synaptic.   That's how I did mine.

---

### Post by avtolle on 2009-02-13
Use Tab to put the cursor on the OK, then hit Enter; you should be good to go from there.

---

### Post by Committed on 2009-02-13
> **NetworkGuy said:**
> Tab??   Enter Key?

I would honestly just do the installs from Synaptic.   That's how I did mine.

Well unfortunately window got closed as I tried to approve.  

Now I tried to go back to Synaptic and it says Unable to get exclusive lock.  Says application is already running.  Damn. I'll have to work on this later.  I've got to go now.  Thanks for the help.

---

### Post by NetworkGuy on 2009-02-13
You can only have one package manager open at a time.   Synaptic can not be open with apt-get or aptitude is running from the command line.

---

### Post by Committed on 2009-02-13
Ok I'm back for a bit.

Rebooted, then tried to open Synaptic package manager and it says this: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Here is what I followed, then got the needs approval from Sun, then accidentally closed the window. Argg

> Before you begin, you need to ensure that your repositories are up to date by issuing the following:
sudo apt-get update



If you are developing Java applications, you will require Java Development Kit (JDK), on the other hand if you just require Java to run Java applications, then you need just Java Runtime Environment (JRE). For the former, the command is as follows:
sudo apt-get install sun-java6-jdk sun-java6-plugin

For JRE:
sudo apt-get install sun-java6-jre sun-java6-plugin

Once either one is done, run the sudo update-java-alternatives -s java-6-sun command and finally add the line “/usr/lib/jvm/java-6-sun” to the top of the /etc/jvm file (gksudo gedit /etc/jvm). Save and exit. To test your Java(TM) setup in the terminal type:-

java -version



If you get an output like below, then you are done!

java version “1.6.0&#8243; Java(TM) SE Runtime Environment (build 1.6.0-b105) Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

---

### Post by avtolle on 2009-02-13
If you've not done this, first open the terminal and ```
sudo dpkg --configure -a
```to (hopefully) take care of the problem.

EDIT: Close Synaptic first.

---

### Post by Committed on 2009-02-13
Thanks, did that and started over.  Everythings installing,got past Sun approval this time.  Should be good to go.

---

### Post by Committed on 2009-02-13
Awesome!  Thanks so much for the help.  All my stock tickers are now working.  I'll learn my way around Linux.  Can you believe it, I used to be a programmer 25 years ago with Cobal and Fortran etc and now I need simple help with installing Java, lol.  Really dated myself there.

Thanks again.  More of my machines will probably end up with linux.  Really liking it so far.  Like anything that's not microsux.

---

### Post by avtolle on 2009-02-13
Did a bit with Fortran "back in the day" myself. So, you're not dating yourself; as far as I'm concerned, we just have a bit more experience, that's all. Good to hear it's all up and going.

---

