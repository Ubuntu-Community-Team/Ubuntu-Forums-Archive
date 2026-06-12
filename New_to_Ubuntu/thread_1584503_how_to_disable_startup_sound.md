---
title: "how to disable startup sound?"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by sallam on 2010-09-29
Greetings

How can I disable the ubuntu startup sound please?

---

### Post by Hippytaff on 2010-09-29
There should be something in startup manager. If you haven't got startup manager
 
```
 
sudo apt-get install startupmanager

```

---

### Post by clive littlewood on 2010-09-29
Hi

Just goto System > preferences > sound and in the box that opens you will see sound themes.

Change to no sound.

Hope that helps

Clive

---

### Post by sallam on 2010-09-29
I saw that before, but wouldn't this disable all system sounds, like warnings and whats not? I only need to disable startup sound alone.

---

### Post by formaldehyde_spoon on 2010-09-29
If you mean the drumbeat on lgin, you need to do this:

sudo -u gdm gconftool-2 --set  /desktop/gnome/sound/event

---

### Post by hoooootz82 on 2010-09-29
if you mean the little drum solo, just go to System->Preferences->Startup Applications , and there you'll see GNOME Logon Sound, Just disable it.

---

### Post by sallam on 2010-10-01
You start your computer, and once ubuntu starts, there is a startup sound, its not a short drum beat, its about 5 sec of loud music, that sounds like waves..

How do I disable it?

---

### Post by sallam on 2010-10-01
I've found the answer [here]("http://www.liberiangeek.net/2010/07/disableturnoff-startup-booting-sound-ubuntu-10-04-lucid-lynx/").

go to System &#8211;> Preferences &#8211;> Startup Applications
Next, select &#8216;Gnome Login Sound&#8217; and uncheck the box

Next, go to System &#8211;> Administration &#8211;> Login Screen
Click Unlock
Uncheck the box to &#8216;Play login sound&#8217; and close out.

Thanks everyone.

---

### Post by beew on 2010-10-01
Yeah, that is a very annoying sound. Why can't they make something more pleasant? 

BTW, it is very simple to disable the sound (as someone has pointed out and the OP has eventually done). I don't know why there are always people  telling beginners to type some gibberish in the terminal for simple things that can be done much more intuitively with the gui. No, it is not easy to use the cli if you don't remember the commands or prone to make typos. It doesn't even contribute to learning when you only cut and paste and have no clue what is going on. End of rant.

---

### Post by sallam on 2010-10-02
beew,
I'm glad I read your reply. I was thinking maybe there is something wrong with me. lol.
Thanks for your encouraging words.

---

### Post by QLee on 2010-10-02
[QUOTE=beew]...
 I don't know why there are always people  telling beginners to type some gibberish in the terminal for simple things that can be done much more intuitively with the gui. No, it is not easy to use the cli if you don't remember the commands or prone to make typos. It doesn't even contribute to learning when you only cut and paste and have no clue what is going on. End of rant.[/QUOTE]
I see that neither you nor sallam have been around these forums for too long, (at least by your signup date), perhaps I can offer some insight into this issue. True that this is a beginners forum, think of the significance of that, there are a lot of beginners here. When someone is a beginner, yet wants to help, many times they don't know the correct answer but they don't realise that the only answer they know isn't the correct one for this specific case. Couple that with the often very confusing reports of a trouble that other beginners make, (and sometimes even erroneous reports or errors in describing), and it isn't too surprising that some of the people trying to help aren't very effective. That's just a fact about open public forums, just like in meatspace, people's knowledge, experience and ability differ. One usually gets a diverse set of answers to a question in real time too, but in our lives we often know who to ask and attend to.

Helpers often choose the CLI because it is often the shortest way to an answer or fix. It isn't as prone to differences in Desktop Environment. So the difference in the path to a menu item, for example between GNOME and KDE, isn't involved.

Another factor, many of the most knowledgeable and experienced helpers like to see effort on the beginners part, some indication that the person is trying to help themselves. Sometimes the "attitude" that a poster exhibits will cause possible helpers to just move on to the next thread, sometimes a poster who makes it a standard practice to always ask simple questions that illustrate that they aren't trying to help themselves or reading any of the help offered or manuals, could be passed over by some of the best helpers. That's just a fact of life, sometimes teachers give the best help to the best students. I think that's probably one of the reasons for the "stickies" at the top of the absolute beginners topics sub-forum which try to explain where to find documentation and how to ask for help but most people don't read them.
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

In the old days, and perhaps today in some places, inexperienced users aren't treated well. I assume it still happens because I see lots of posts that ask to be treated nicely because they are new. With Ubuntu, the forum admin encourages a spirit of humanity, "n00bs" aren't forced to pass any initiation and usually get pretty good help. The first answer isn't always the best, some people will have misunderstood the question, some people won't have read through the whole thread, some aren't yet able to troubleshoot effectively, and some probably are here for their own agenda rather than wanting to help. In short, a microcosm of the real world, it's not like a "help line" where customer service reps are paid to help a client, so here people are free to help as they choose, this also includes free to not help. In my opinion, people should post in a manner which encourages others to help but that is not easy to define. We need to also remember this is a users forum, we're being "staffed" by users, not reps of any operating system. However, it's generally a pretty calm environment in which to ask questions.

I hope that can help to explain some of the issue you raise.

Edit: I'm sorry, I meant to add this to my original reply but, when I look back over it, I see I didn't. In many areas there is a local LUG (Linux Users Group), usually they will meet at least monthly and often people can bring their systems and get one-on-one support. If I was new at this, I would probably see if there is one in my area. Of course, there is also paid support available but usually that is accessed by enterprise customers (companies) rather than a simple desktop user. I just wanted to mention these two options that don't often get mentioned in the forums but which may be helpful for some users.

---

### Post by qQChtIhpk1 on 2011-06-01
This is exactly the help i need, but it doesn't work.

First, i uncheck the Startup Application, Gnome Login Sound.

Next, i "go to System –> Administration –> Login Screen
Click Unlock, "Uncheck the box to ‘Play login sound’ and close out."

However, the Unlock does not work and i cannot see the options on the screen to uncheck "Play login sound".

Help would be appreciated - Thank You!

Chazbo

---

