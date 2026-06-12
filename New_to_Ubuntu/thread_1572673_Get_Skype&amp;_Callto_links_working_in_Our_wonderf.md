---
title: "Get Skype&amp; Callto links working in Our wonderful Lucid"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by impresionist on 2010-09-11
Hi All,
I was really long turning into the issue to get working the skype links, and the callto links to work in Firefox under gusty,festy,hardy, and lastly un der LUCID, just now I got it, so I decide to share this thread for commun help.

So, the issue that after you install your skype, via synaptic, and you try to open any link coded as: skype:username?call, or any phone number as: callto:+34911111111, you'll get an error message from Firefox saying that:
> 
Firefox doesn't know how to open this address, because the protocol Skype isn't associated with any program.


So, let's go:
[LIST]
[/LIST]] After installing skype, verify that you have all correct, so run:
> 
whereis skype


You should get:
> 
skype: /usr/bin/skype /usr/share/skype

[LIST]
If yes, it's mean that you have correctly Skype installed and located, so before follow, run skype, and login your user season.
[/list]
[LIST] We have to download the Skype handler from Philipp kolmann repository, so we're going to use v. 1.0, open terminal, and issue:
> 
wget [http://www.kolmann.at/philipp/linux/skype_action_handler/action_handler_1.0.py](http://www.kolmann.at/philipp/linux/skype_action_handler/action_handler_1.0.py)

[/LIST]
[LIST]Now we have been downloaded the script, so let's go:
> 
sudo cp '/Desktop/action_handler_1.0.py/' '/usr/local/bin/'

[/LIST]
[LIST] Change permission with:
> 
sudo chmod +x /usr/local/bin/action_handler_1.0.py

[/LIST]
[LIST]Then create a symbolic link
> 
sudo ln -s /usr/local/bin/action_handler_1.0.py /usr/local/bin/skype_action_handler

[/list]
[LIST]
Now we have all done, let's try if it's working, so run:
> 
skype_action_handler skype:echo123?chat

[/list]
You'll get a skype window asking you that another application are trying to access to skype, BEFORE accepting, confirm to do the same every time, and accept, so you'll get a chat window with skype testing service, it's mean, CONGRATULATIONS, it's work, BUT that's not all.
[/LIST]
[LIST]
> 
skype_action_handler skype:echo123?call

[/list]
[LIST] Do the same as previous step to fix the calling service.
[/list]
[LIST]
Now we need to add the service, so issue:
> 
gconftool-2 -s -t string /desktop/gnome/url-handlers/skype/command '/usr/local/bin/skype_action_handler "%s"'

> 
gconftool-2 -s -t bool /desktop/gnome/url-handlers/skype/enabled true

[/list]
[LIST]
So, after this point, you have your skype correctly working and you can test just clicking in my skype user [here]("skype:softbrocker?call"), you should get directly the skype calling window, if yes, Congratulations, BUT that's not all.

Because you will get working only the Skype links such as skype:echo123?call, and skype:echo123?chat... But if you'll see a link like: callto:+349188888888, you'll get a Firefox window asking you to choice the application within you want to open the link, in this case you have to open the selector, and go to /usr/local/bin/, and then choice action_handler_1.0.py, and BEFORE confirm that, click to remember your selection, to get that working automatically next time, if done, you should click here, and you have to get the skype caller window, if you, now CONGRATULATIONS.
Work in box under Ubuntu Lucid& Firefox 3.6.9
Work like charm in Sugar CRM phone numbers.
[/list]
I if you want that your Firefox recognize automatically all numbers as callto:XXXX, you have to add the preference to about:config in Firefox. I don't do it for myself, so I don't recommended, because in this case, you'll see all numbers in web as phone numbers, meanwhile they are not phones, such as SIC code, and all codes, you'll get them as callto:XXX links, which is not a great functions!

Enjoy!):P

---

### Post by gdi2k on 2010-11-19
Awesome, just what I was looking for, thanks. 

I would be interested in being able to click on phone numbers directly from Gmail Contacts for example, maybe you could add it to the guide as an option for those that prefer it.

---

### Post by yasir.elsharif on 2010-12-12
[impresionist]("http://ubuntuforums.org/member.php?u=594859"), You are a star
Thanks a lot, this is very strait forward solution, and it just works!
Thanks

---

### Post by impresionist on 2011-02-22
Hello guys,
After disappointment and full down quality of skype, we decide to jailbreak from Skype imperious. So for who want to follow us this jailbreak, I wrote another thread solution for click to call for Twinkle SIP softphone, you can find it here: [http://www.softbrocker.com/forum/twinkle-clikc2call-firefox/](http://www.softbrocker.com/forum/twinkle-clikc2call-firefox/) 

Regards,

---

### Post by slaykristian on 2011-07-15
Hi Impresionist!
Any news about this solution in Firefox 5 under Natty Narwhal?!
It seems that there's a different python library version.

I hope you'll find early a usefully solution!!!
You're great!!

Good work!
Thanks in advance!
Bye!

---

### Post by Bucky Ball on 2011-09-29
Thanks, worked a treat for me in 10.10. Just having a look at Twinkle ...

---

### Post by impresionist on 2011-09-29
> **slaykristian said:**
> Hi Impresionist!
Any news about this solution in Firefox 5 under Natty Narwhal?!
It seems that there's a different python library version.

I hope you'll find early a usefully solution!!!
You're great!!

Good work!
Thanks in advance!
Bye!

Sorry, slaykristian, I didn't upgrade to Naatty, as Lucid still alive as LTS yet, so I cann't answer you for that. But in theory, where's is the problem??

---

