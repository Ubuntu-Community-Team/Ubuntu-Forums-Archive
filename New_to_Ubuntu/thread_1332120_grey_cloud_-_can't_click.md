---
title: "grey cloud - can't click"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by dbch on 2009-11-20
I installed a bunch of firefox addons at once and then the screen kept clouding over grey and I couldn't click on anything.  Mouse still moved.  It would last for quite a few minutes.
And everthing was slow.

I disabled noscript, wot and adb.  Seems faster now.  Still getting clouded but just for a few seconds.

Anthing I should NOT be adding from firefox on Ubuntu?

Worse - when I'd force quit it, and then try to restart firefox, I'd get the message that it was already running and that I'd have to shut it down or restart.  I'd restart because there was nothing there to shut down and then the computer wouldn't shut down.  I had to unplug it.  

I tried running recovery mode and repair packages.  It read that I might try the command run apt-get update.

I don't know what to do and I typed it in the accessories terminal.  Got no such command.

What am I doing?

---

### Post by lavinog on 2009-11-20
Does disabling all addons fix the issue?

---

### Post by dbch on 2009-11-20
I googled it for awhile.  Found this:

**Do your windows turn grey often?**

                    	       If you are like me, in Hardy, quite a bit of time my windows grey out etc waiting for a response. Also if you run synergy, synergyc probably isn&#8217;t even close to usable unless you run it as root. Also this causes some audio stuttering. 
 **The problem**
Improper configuration of the new kernel scheduler broke a lot of things. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188226](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188226)
 **The good news**
If you use ubuntu-server kernel, or have hardy-proposed repository enabled, this resolves it.




Don't know what it means.


Then somewhere someone wrote to get compizconfig, the advanced desktop.  I got everthing I could in synaptic.  Seemed good.
Then I got the grey again and the system prompted for a force quit.
Firefox reloaded ok.


Wierder too - before I put in compizconfig, I tried to minimize firefox to browser and it went, and then popped back open again.  I had to unplug the computer again to get out of it.


I could try disabling all my addons, it would take some time though.


Anyone know for sure?


Thanks.

---

### Post by dbch on 2009-11-20
Someone's got to know what's going on right?

And even after putting in compizconfig, I still get the firefox window popping back open when I minimze it.

Plus the grey.

I found this:

**[Unable to *minimize pop* up *window* / *window*.*open* - CodingForums.com]("http://codingforums.com/showthread.php?t=99624")**

7 posts - 3 authors - Last post: 31 Oct 2006
Unable to *minimize pop* up *window* / *window*.*open* JavaScript programming. **...** Make the switch *Ubuntu* Linux. Spookster is offline **...** The *window* continues bouncing *back* up when ever the user tries minimizing it. **...**
[IMG]http://ubuntuforums.org/data:image/png,%89PNG%0D%0A%1A%0A%00%00%00%0DIHDR%00%00%002%00%00%00%07%02%03%00%00%007%E6%F6%3C%00%00%00%03sBIT%08%08%08%DB%E1O%E0%00%00%00%0CPLTE%FF%FF%FF%FF%FF%FF%CC%CC%CC%A7%D3%A7Mz%23%09%00%00%00%04tRNS%00%FF%FF%FF%B3-%40%88%00%00%00%09pHYs%00%00%0B%12%00%00%0B%12%01%D2%DD%7E%FC%00%00%00%16tEXtCreation%20Time%0005%2F01%2F08%FA%82%27%90%00%00%00%18tEXtSoftware%00Adobe%20FireworksO%B3%1FN%00%00%00%22IDAT%08%99ch%60%60%00%22%05%28Z%85%04%160%EC%FF%0F%06%A1%20%90%80%97%87%AA%0F%C5L%00%05%07.7%04%2Fj%BB%00%00%00%00IEND%AEB%60%82[/IMG]codingforums.com › ... › [JavaScript programming]("http://www.google.com/url?q=http://codingforums.com/forumdisplay.php%3Ff%3D2&ei=a20GS-fWKY2wswPg6uXACQ&sa=X&oi=breadcrumbs&resnum=2&ct=result&cd=1&ved=0CAkQ6QUoAQ&usg=AFQjCNGZqvsI3_CGlh6oVSwxHnVUqUGUuw") -  [[IMG]http://tr.xmarks.com/tracking/impressions.gif?mid=g24tyy2r&sess=g28tdkx9&product=searchtabs&app=serp&page=serp.shmear&shmearname=help%20forums.window%2520pops%2520back%2520open%2520on%2520minimize%2520ubuntu&cache=0[/IMG]#8 in Help Forums]("http://www.xmarks.com/topic/help%20forums?sid=g28tdkx9&product=searchtabs&cid=serp.schmear&mid=g24tyy2r")

But its all code.  

There's gotta be another way to do this and the grey/nonresponse too.... ?

---

