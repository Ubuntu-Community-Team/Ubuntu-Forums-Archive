---
title: "Firefox 3.5"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by Anybloodyid on 2009-11-29
Hi
 I'm using Ubuntu9.10 and I'm having problems with Firefox version3.5.5 Mozilla Firefox for Ubuntu canonical - 1.0
Some of the sites I visit work OK and others have problems one of them is ebay it starts load but then keeps waiting for something on the page to load, which it never does.
Another site is my own which works until I try to view one of the forums then I get this message
 You have chosen to open viewforum.php
which is a PHP file
from [http://www.poem-n-verse.co.uk]("http://www.poem-n-verse.co.uk/")
What should Firefox do with this file
 I'm thinking this could be the problem with other pages, maybe they need to use PHP but Firefox is not letting them.
Had to use daughters computer as the Submit new thread button is not responding when I try to post from mine.
 What do I need to do to get all sites working again?
 Thanks for looking

---

### Post by kellemes on 2009-11-29
> **Anybloodyid said:**
> Hi
 I'm using Ubuntu9.10 and I'm having problems with Firefox version3.5.5 Mozilla Firefox for Ubuntu canonical - 1.0
Some of the sites I visit work OK and others have problems one of them is ebay it starts load but then keeps waiting for something on the page to load, which it never does.
Another site is my own which works until I try to view one of the forums then I get this message
 You have chosen to open viewforum.php
which is a PHP file
from [http://www.poem-n-verse.co.uk]("http://www.poem-n-verse.co.uk/")
What should Firefox do with this file
 I'm thinking this could be the problem with other pages, maybe they need to use PHP but Firefox is not letting them.
Had to use daughters computer as the Submit new thread button is not responding when I try to post from mine.
 What do I need to do to get all sites working again?
 Thanks for looking

Have you tried emptying the Firefox cache?

---

### Post by u.b.u.n.t.u on 2009-11-29
I have loaded the site [http://www.poem-n-verse.co.uk/](http://www.poem-n-verse.co.uk/) without problem using Firefox 3.5.5.

Have you recently installed an addon for Firefox or made some changes to it?

It sounds like either a configuration error, corruption, or an incorrect type association within Firefox.

---

### Post by Anybloodyid on 2009-11-29
Hi  Thanks for the replies  Don't think its anything to do with the cache as I've tried using Google Chrome and Opera and the same thing is happening. I too can load Poem-n-Verse no problem, it's when I try to click on a members forum that I get the message but not always. Clicking on ebay doesn't work either but that just doesn't load at all. It's like clicking the submit button on here nothing happens.  So it I think it's a scripting problem.  Will have to submit this using Daughters computer again.

---

### Post by u.b.u.n.t.u on 2009-11-29
> **Anybloodyid said:**
> when I try to click on a members forum that I get the message but not always.

When I click on the "Forum" link, the new page states "This board has no forums."

I did ask you some questions, but you didn't answer them.

Q1 Have you installed any addons for Firefox recently?

Q2 Have you made any changes to Firefox recently?

It may be that you have enabled some developer, debugging option somewhere. Hence you are given the option to work in PHP.

Could you take a screenshot of the problem, upload it to:

[http://imageshack.us/](http://imageshack.us/)

Then give the link here. It may assist to better understand what is happening.

---

### Post by Anybloodyid on 2009-11-30
Hi   U.B.U.N.T.U  When I click on the "Forum" link, the new page states "This board has no forums." 
You can ony see the forums if you are a member, but I don't think it's the site as I can use daughters computer at the site with no problems at all.  

Q1 Have you installed any addons for Firefox recently?  No

 Q2 Have you made any changes to Firefox recently? Before I upgraded I used the Firefox version from Ubuntuzilla after upgrade it stopped working correctly so I uninstalled it and went back to the one that comes with Karmic. 

Can't upload screen shot because when I hit the submit button at Image Shack nothing happens same here when I hit Submit Reply. 
This is why I have to use Daughters comp to ask a question.  This is why I have to do everything on Daughters Comp.

Thanks 
[IMG]http://img268.imageshack.us/img268/2237/errorqt.gif[/IMG]

---

### Post by u.b.u.n.t.u on 2009-11-30
Anybloodyid it seems as though you have Firefox in some sort of developer, debug mode.

I have been unable to find a similar situation that also provided a solution.

Are you able to completely uninstall Firefox and then re install it? It is important that your Firefox profile be deleted and then recreated with default settings.

Alternatively are you able to install a different browser to see if the problem exists? If it doesn't, then at least we know it is likely limited to Firefox itself.

---

### Post by Anybloodyid on 2009-11-30
Hi

I'm trying to send this using Chromium 4.0.259.0 (Ubuntu build 33225)

Let's see if it works.

---

### Post by Anybloodyid on 2009-11-30
Hi

I'm trying to send this using Chromium 4.0.259.0 (Ubuntu build 33225)

Let's see if it works.
If it does what's the best way to remove Firefox should I do it with the Synaptic Manager and if I do does that get rid of the profile as well?

---

### Post by paydaydaddy on 2009-11-30
my guess is that you need to turn off ipv6 in firefox. I don't remember the specifics of how it is done, but it is a common and well documented problem. I am leaving for work and don't have time to look it up, but a search of the forum or a google search should give you the answer.

---

### Post by steve161 on 2009-11-30
I'm not sure what turning off ipv6 will do to help, but you can enter about:config in the address bar, acknowledge the void the warranty joke, enter ipv6 in the search box, and click on disable ipv6 so it reads true.
You may also try to just delete the mozilla folder in the home directory before you do a complete reinstall of Firefox.  That is usually the source of many problems.  Open your home folder, click view, click show hidden files, look for the mozilla folder, and either move to trash or rename.

---

### Post by Anybloodyid on 2009-11-30
Tried this  
 A different option that I think should work both with Karmic and older releases.  
 

 ```


 sudo gedit /etc/sysctl.d/60-ipv6.conf  
 
```

 This is a non-existant file so it should open gedit with a blank file named 60-ipv6.conf, to which you add the text....  
 

 ```

 

 #Disable IPv6  
 net.ipv6.conf.all.disable_ipv6=1  
 
```

 Then save the file. Since this is a file that is not managed by the system, you should not have to worry about doing this again because some update replaced the file.  
 

 To activate the change without rebooting you should be able to type the command:  
 

 ```

 

 invoke-rc.d procps start  

```


 

 To see that IPv6 is actually disabled type the command:  
 

 ```

 

 cat /proc/net/if_inet6  
 
```

 If the above command does not show any output, then ipv6 is disabled.  
 It Didn't so I guess it's disabled.  
 

 Then did this.  
 

 And to avoid Firefox trying to ask the router (that might have been set up as a LAN DNS server) to solve any ipv6, I would run Firefox and type in the address bar:  
 Code:  
 

 about:config  
 

 Then, in the filter field of the new window, just type  
 ```

 ipv6  
 
```

 That will filter out everything but (currently) just two lines. Double click on  
 ```

 network.dns.disableIPv6  
 
```

 to set it to true.  
 From now on, even Firefox will not try to secretly(?) annoy you or your network with any ipv6 query.  
 

 Then finally did this  
 > You may also try to just delete the mozilla folder in the home directory before you do a complete reinstall of Firefox. That is usually the source of many problems. Open your home folder, click view, click show hidden files, look for the mozilla folder, and either move to trash or rename.
 Still no luck when I go to ebay and click on sign in enter my details and it just keeps trying to load but never does.  
 Even clicking on Post Quick Reply here  doesn't work.  
 Posting this from Daughters Computer which has no problems at all with any site, she is using Vista, Don't realy want to go back to windows but might try Another Linux Distro to see how things go.  
 

 Last try to post using Chromium.
 Didn't work so still using Daughters Comp

---

### Post by naiku on 2009-11-30
Your problem sounds very similar to one I am having, for example if I watch a You Tube video, after the video plays, a couple links to other videos appear in the middle, if I click on these nothing happens, same with Facebook video, if I watch a video, when the Play Again link appears, nothing happens when I click it. 

If I go to the Nike store website, and use the menu to go to Mens > Shoes and click on Shoes, nothing appears in the main section of the screen, nothing tries to load, it just does nothing. I will give the sites you listed a try when I get home and see if they work for me.

---

### Post by u.b.u.n.t.u on 2009-11-30
Is Chromium having the same problems as Firefox?

---

### Post by Anybloodyid on 2009-11-30
Yes, Chromium and Opera both doing the same.

Begger me just tried to post this with FF and it worked!!

Wil go and try eBay.

Well it's sti playing up!

---

### Post by u.b.u.n.t.u on 2009-11-30
If all of the browsers are acting in a similar manner, then that would suggest that some other setting is to blame, specifically the operating system.

As you are using Ubuntu 9.10 and it is a new release, are you able to say whether these browsers issues existed immediately or shortly after the installation?

---

### Post by Anybloodyid on 2009-12-01
Yes It's the new stable release of 9.10 and this started happening straight after the update from 9.04. Which worked no problem if I could roll back I'd do it in an instant. 
Reading the forum it would appear that there are many others having the same problem since upgrading to 9.10.


 And today it's decided not to post to the Ubuntuforums so I'm back on Daughters computer!

---

### Post by u.b.u.n.t.u on 2009-12-01
The only consolation is that it will be fixed and applied as an update to download.

---

### Post by Anybloodyid on 2009-12-02
Thanks for all the help but by the time a fix is found I and a few others, I suspect, will be using another version of a Linux Operating System.

---

### Post by Anybloodyid on 2009-12-02
Well it's all sorted loaded windows 7 and all working!

---

### Post by u.b.u.n.t.u on 2009-12-02
> **Anybloodyid said:**
> Well it's all sorted loaded windows 7 and all working!

Good!

---

### Post by oldgeekster on 2009-12-02
> **paydaydaddy said:**
> my guess is that you need to turn off ipv6 in firefox. I don't remember the specifics of how it is done, but it is a common and well documented problem. I am leaving for work and don't have time to look it up, but a search of the forum or a google search should give you the answer.I agree with you paydaydaddy.  Easiest thing in the world and certainly worth giving a shot.

Open Firefox and in the URL window type:
About:Config
and hit Enter

After assuring the popup you will be careful, scroll down to:
network.dns.disableIPv6

If it is not already set to "True", Right-click on it and select "Toggle" then it should be.

Close/re-open your web browser and surf to test the speed as you move from site to site.  

This was the ONLY change I made on my Karmic Koala system after upgrading to it and it did away with all of the sluggishness I had previously been experiencing in FireFox (now using version 3.5.5 from canonical and very happy with it).

Of course his/her mileage may vary, but worked for me. :popcorn:

---

