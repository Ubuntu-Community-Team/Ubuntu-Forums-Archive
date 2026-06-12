---
title: "Need help with wireless card"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by jspivey on 2010-06-15
I am absolutey new here.  How do I get started?  I am reading books on how to use wireless in Ubuntu but nothing explains in detail step-by-step how to load the drivers for the wireless card.
 
The Ubuntu OS does not see the card. Finally figured out where the Network Manager utility was located, what it actually looks like.  When I RIGHT CLICKED on it could not click on "connection information" which sucked. So am still stuck with no real help.
 
I read everywhere about how good Ubuntu is but what is not stated is HOW FRUSTRATING it is to get started with it or get answers in DETAIL to get something to work.

---

### Post by bodhi.zazen on 2010-06-15
Hardware problems are frustrating.

First, can you temporarily use a wired connection ?

Second, what wireless card do you have ? Some cards work better  then others and as painful as it sounds you can get a Linux compatible wireless card for as little as $20.

Wireless is a bit more complex as there are issues of WEP / WPA etc as well.

See: [https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

As you work though that page, ask questions if you get stuck.

---

### Post by marcoftheknight on 2010-06-15
[I]

got to APPLICATIONS-->ACCESORIES-->Terminal and copy and paste this code:

[/I]sudo lshw -C [I]network

Then post the results on the forum thanks
[/I]

---

### Post by QIII on 2010-06-15
First -- If you encounter people who are impolite or unhelpful, ignore them.  There are a few.

Second -- Remember that we are all here on our own time, we are volunteers and we are here when we have the time.  You may ask a question that someone has a perfectly good answer to, but he may be in Bangalore or New South Wales or Holland or Brazil.  He may not be awake when you are or may be at work when you post your question.  Be a little patient and understand that.  Your question may or may not be answered in five minutes.  If it is not answered within 24 hours, feel free to "bump" the question by adding a response to it to get it back up to the top of the queue.  Please remember that when you bump you push someone else down in the queue, so be considerate.

Phrase your question as a question rather than a gripe.  You catch more flies with honey than with vinegar.  Someone who might otherwise be willing to help might move on if you are ranting.

We are here to help and we will do our best.  Some things are more difficult than others and they will sometimes take a bit of troubleshooting and back and forth.  Answers are rarely as simple as "Type this an push enter."

For example, bodhi.zazen directed you to a URL.  Often, the question you are asking has been answered in detail elsewhere.  You will notice that he also said to come back if you have questions.  He's not saying "RTFM and go away".  He's pointing you to a helpful resource and offering help from there if you need it.  

marcoftheknight asked you do do something that will give us some information that might be helpful in diagnosing the problem.  If you don't understand what he is asking you to do, let him know that you don't understand and give him the opportunity to be more helpful.

Also remember that as much as we try to understand that others have less experience, it is human nature to assume that someone else is understanding you when you spout off a long answer.

If we do that, just smack us on the side of the head and tell us to slow down and be more basic.

Welcome to Ubuntu.  Disregard the jerks.  They are uncommon, but they do exist.

---

### Post by oldsoundguy on 2010-06-15
As a tip, do your searches for topics using Google and not the built in search engine.  You will get better results right now until they get the search engine working better.

---

### Post by spotted zebra on 2010-06-15
jspivey: don't get bummed. a lot of the people helping here are helping a lot people usually with similar problems and we are doing it for free. it can be aggravating sometimes because the answer to your problem is just a google or search function away and we know that and sometimes expect you to solve the problem on your own. 

we love to help everyone and in turn be helped by those who know more than we do. i my case that is about everyone here. but i try to help those who i can. 

i can be frustrating to find a specific answer to a specific problem. sometime you have to read and read and read and read some more to find what you are looking cause i promise it is on the Internet finding sometimes just takes a while. 

try changing up your search criteria or thinking about your search terms from a different point of view. searching for information is an art.

and everything that QIII said.

don't get down just take a break, do something else for a while and come back at it.

---

### Post by Mark Phelps on 2010-06-15
> **jspivey said:**
> I am absolutey new here.  How do I get started?  I am reading books on how to use wireless in Ubuntu but nothing explains in detail step-by-step how to load the drivers for the wireless card.
Generally speaking, virtually nothing in Ubuntu (or in any other OS for that matter) is a simple click-to-fix solution.  OS versions come into play, hardware versions come into play, drivers come into play.  What will happen (in the best cases) is a back-and-forth exchange where you are asked for details, you provide them, you are asked to try something, it may not work ... and if not, the process starts over.

So, rather than provide you a 200-page "handbook" on all POSSIBLE solutions, we need to get detailed info so we can provide a solution that will work for your specific case.
 
> I read everywhere about how good Ubuntu is but what is not stated is HOW FRUSTRATING it is to get started with it ...
It can be VERY frustrating, because, in fact, ALL of us had to start where you are now and learn our way up the technology ladder.  When you finally know HOW to do something well, it's easy to forget how difficult it was to learn it originally.

It's especially frustrating if you come over from MS Windows or a Mac and expect everything here to look and behave exactly the same ... which it does not.  Things that are slightly different are often harder to learn than things that are very different.

>  ...get answers in DETAIL to get something to work.

Well, that's why we have these forums.

---

### Post by HermanAB on 2010-06-15
Well, bear in mind that Ubuntu is not the easiest Linux distribution.  It is sort of intermediate.  If you want to use Ubuntu, then you need to be prepared for some pain.  

If you cannot take it, install one of the older desktop distributions such as Mandriva or Suse.  Those two have wizards for everything, including ndiswrappers (the mechanism for using a Windows WiFi driver on Linux).

---

### Post by QIII on 2010-06-15
One thing I forgot to mention:

One reason that hardware problems can be such a pain is that some people  have the mistaken impression that OSs support hardware.  They don't,  but Microsoft would like you to think they do.

Windows doesn't support hardware.  Hardware OEMs write drivers that are  compatible with Windows.  They do that because the money is there.  If  90% of your customer base is using Windows, where would you spend your  effort?  Do you blame them?

The real issue is that hardware OEMs often do not create drivers for  Linux.  Some that do don't produce very good ones.

That doesn't lessen your frustration.  I understand that.  What we often  do is try to find out how to make something work in spite of the lack  of support.  Sometimes a clever open source developer comes up with a  driver that will work.  Sometimes not.

Sometimes, unfortunately, "Buy a Linux compatible card" is the only  answer in our world for now.

---

### Post by oldsoundguy on 2010-06-15
Another thing to remember .. if you are changing because Windows just does not work for you, good chance that Linux will not work that well also.  Hardware issues are hardware issues and are platform independent.

The saying that Linux is NOT Windows is the first thing you should memorize!

---

