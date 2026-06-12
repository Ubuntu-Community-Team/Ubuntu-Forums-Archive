---
title: "No access to website java applet"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by BeachBuddah on 2010-11-08
Hello all - I'm trying to use a website [www.jmeeting.com](www.jmeeting.com).  There is a java applet that is supposed to run to see the chat rooms and cams but every time I go to the site I get an error message "Exception starting applet".  I have installed the sun jave -jre from the Synaptic package manager and am unsure what to do next.

Thanks in advance,

Chris

---

### Post by cromat on 2010-11-08
You need to make sure that the Sun JDK / JRE is the default one being used.

```
sudo update-alternatives --config java
```

Then make sure the sun one is the selected option.  That is usual problem I have run into.

---

### Post by BeachBuddah on 2010-11-08
Cromat

Thank you for your response.  I did as suggested and I DO now have Sun Java as my java platform but it didn't help with jmeeting.  I still get the same error panel coming up.  

I'm not sure what to do here, since it offers me the option of a report but it's lengthy - should I post it?

Chris

---

### Post by cromat on 2010-11-15
Yes post it, it might be the only clue as to what is the issue.

---

### Post by 311005901 on 2010-11-15
Make sure you put the report in the code quotes, or it may be formatted incorrectly.

---

### Post by BeachBuddah on 2010-11-23
Hi - sorry for the delay in my response.  Anyway attached is a screenshot of the log file that is generated when I try to login to the site.  Sorry but I couldn't figure out how to post the file in here...

All seems to be well until the nasty exception comes along and stops the process dead in it's tracks.

I don't think I have any other problems with the Sun Java package.  Someone suggested it might be a problem with their code at the site.  Ideas?

---

### Post by BeachBuddah on 2010-11-29
Any clue, anyone?

---

### Post by lykeion on 2010-11-29
Try to uninstall IcedTea Java browser plugin:
```
sudo apt-get remove icedtea6-plugin
```
And make sure you have installed Sun Java browser plugin:
```
sudo apt-get install sun-java6-plugin
```
Finally restart your browser and try again

---

### Post by BeachBuddah on 2010-11-30
Lykeion!

Truly amazing - I never even heard of Iced Tea, let alone realized I had it installed.  But it made all the difference. (I already had gotten the Sun Java installed)  But now it works.  Thank You very much.

---

### Post by lykeion on 2010-11-30
Great that it worked out for you. Could you please tag this thread as [SOLVED]("http://ubuntuforums.org/showpost.php...51&postcount=6") to let others find solutions easily.

---

### Post by UbunteroCENCAL on 2011-03-27
...no so fast in declaring victory!!!...I've been trying all day and after having removed everything and installed the newest versions of jre and java-plugin, I still cannot get java applets to work on either chrome or firefox...
Anyone else with the same problem? or even more fun, anyone with a solution??

Tante grazie

---

