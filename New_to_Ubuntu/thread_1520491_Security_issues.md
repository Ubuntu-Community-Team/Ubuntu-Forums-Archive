---
title: "Security issues"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by new_tew_this on 2010-06-29
I have a security issue with a user on my machine. How can I record their internet activities with ubuntu, so they can't just delete their search history. I am using Ubuntu 9.10 and Firefox 3.5. This person has figured out how to delete their search history and I just happened to catch them using my computer for unauthorised searches on the web. I want to be able to see what has been accessed on the net with my computer when I am not around, even if it was done on another users account. Can anyone help with this?

---

### Post by GreenN00b on 2010-06-29
Why not just disable the other accounts so that nobody can use your computer when you are not around?

---

### Post by mkvnmtr on 2010-06-29
You might find something of interest in the Firefox cache or even in .thumbnails.

---

### Post by bigseb on 2010-06-29
You could always create a whitelist ie a list of sites that _can_ be visited. All other sites would be blocked. You still won't know what they've been viewing but at least  from then on they'll only see what you let them...

---

### Post by bodhi.zazen on 2010-06-29
> **new_tew_this said:**
> I have a security issue with a user on my machine. How can I record their internet activities with ubuntu, so they can't just delete their search history. I am using Ubuntu 9.10 and Firefox 3.5. This person has figured out how to delete their search history and I just happened to catch them using my computer for unauthorised searches on the web. I want to be able to see what has been accessed on the net with my computer when I am not around, even if it was done on another users account. Can anyone help with this?

At the end of the day, it depends on if you or your intruder has more skill. As you have to ask, I am guessing you are on the short end of the stick here.

Your options might include :

1. Perhaps your router can help, some routers will log this kind of information. If not, perhaps purchasing a better router may be the best option.

2. Install a proxy server, such as squid, and restrict web access via iptables.

Better, if a user abuses his or her privileges, remove their access.

If you are being cracked, contact the local authorities.

---

### Post by new_tew_this on 2010-06-29
I only had one account on the computer and it wasn't password protected until now. I didn't want to have to do that because my daughter plays a lot of educational games and stuff on-line. She is young and only knows how to get to them from the bookmark list. Oh well, I guess she will be needing help to get on the puter now. I still want to be able to spy on what other people are doing on here. I can't always be watching over their shoulders. Eventually my 13 and 15 year old boys are going to have to use the puter with no adults around to do school work, hence the reason to want to spy on them. My 15 year old is the one causing all these problems. I caught him because he doesn't know how to clear out the history from the Google search box, just the firefox history.

---

### Post by ibuclaw on 2010-06-29
[http://www.opendns.com/](http://www.opendns.com/) will not protect curious teenagers from all dangers, but it should cover 85-90% of the things out there you don't want them to see.

The rest is all down to local protection.

---

### Post by bodhi.zazen on 2010-06-30
+1 OpenDNS

With the last set of information you posted, I would suggest Dansguardian.

Last piece of advice, nothing replaces parental supervision.

---

### Post by new_tew_this on 2010-06-30
I know direct supervision is the best, but its not always feasible with mine and my wife's work and school schedules. Any way, I found some Firefox add-ons that require a password to delete browsing history. I made separate accounts for the kids, and enabled that add-on on each, along with other controls. I just wish there was a way to disable the "private browsing" option, or to record what is being done, weather it is in private mode or not. Thanks for you help. I installed Squid also btw. Can't be too secure. If you know how to disable that private browsing, I would sure like to know.

---

### Post by QIII on 2010-06-30
Kids are very clever.  You have entered an arms race.

The best you can do is use an arsenal of tools and create a complex lock.  They will pick it, you can count on that.  Add an new tumbler.  When they pick that, add another.

I hate to give advice that costs money, but, as mentioned above, higher end routers can often be used to record history and block/lock access.  With some, you can even extract logs as a text files and search for "nekkidchicks.com".  Or, you can get IP addresses and take a look at them deliberately and block the ones you are uncomfortable with.

If you go that route, just be sure that your user name and password have nothing to do with the family pet, birthdays, relatives' names, etc.  Use special characters.  All the normal user/password advice.  Find out if you can close any back doors.  You can bet little Johnny is going to try to hack your router and he'll talk to his friends if he can't get access to the web from your machine.

Don't be adversarial with your children and see them as an enemy, of course.

We had an adage in the Army:  "Trust, but verify."

---

### Post by ibuclaw on 2010-06-30
> **new_tew_this said:**
> I know direct supervision is the best, but its not always feasible with mine and my wife's work and school schedules. Any way, I found some Firefox add-ons that require a password to delete browsing history. I made separate accounts for the kids, and enabled that add-on on each, along with other controls. I just wish there was a way to disable the "private browsing" option, or to record what is being done, weather it is in private mode or not. Thanks for you help. I installed Squid also btw. Can't be too secure. If you know how to disable that private browsing, I would sure like to know.

You could do the cheeky thing and run:
```
sudo dpkg-divert --local --rename --add /usr/lib/firefox-3.6.6/components/nsPrivateBrowsingService.js
```
That will disable it for ***everyone*** though.

If you run the above, and want to revert it, simply run:
```
sudo dpkg-divert --rename --remove /usr/lib/firefox-3.6.6/components/nsPrivateBrowsingService.js
```







To put the cherry on the cake, you can also remove it from the menu.
```
cp /etc/firefox/profile/userChrome-example.css /home/**USERNAME**/.mozilla/firefox/**PROFILE**/chrome/userChrome.css
```
Then open the copied userChrome.css file and add:
[PHP]#privateBrowsingItem, #privateBrowsingAutoStart {display: none !important;}[/PHP]
Below the @namespace line.

Though is not really necessary.

Regards

---

### Post by bodhi.zazen on 2010-06-30
> **ibuclaw said:**
> You could do the cheeky thing and run:
```
sudo dpkg-divert --local --rename --add /usr/lib/firefox-3.6.6/components/nsPrivateBrowsingService.js
```That will disable it for ***everyone*** though.

If you run the above, and want to revert it, simply run:
```
sudo dpkg-divert --rename --remove /usr/lib/firefox-3.6.6/components/nsPrivateBrowsingService.js
```





To put the cherry on the cake, you can also remove it from the menu.
```
cp /etc/firefox/profile/userChrome-example.css /home/**USERNAME**/.mozilla/firefox/**PROFILE**/chrome/userChrome.css
```Then open the copied userChrome.css file and add:
[PHP]#privateBrowsingItem, #privateBrowsingAutoStart {display: none !important;}[/PHP]Below the @namespace line.

Though is not really necessary.

Regards

That 's evil :twisted:

---

### Post by new_tew_this on 2010-07-03
haha yeah its evil to remove it, but I decided to just deactivate it to make him think he is private browsing, then I can go behind him and see what he has been doing any way. You see they have to have my password now to delete their history :) So now I can be sneaky, and if he doesn't quit looking at porn, then I will remove the option from the menu. This way it gives him a chance to either regain my trust by not looking at it, or screw himself more by continuing with his bad behaviour.

---

### Post by berryjw on 2010-12-03
Hi there.  What extensions are you using to lock/password the history?

---

