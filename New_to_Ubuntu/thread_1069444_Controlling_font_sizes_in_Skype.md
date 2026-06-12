---
title: "Controlling font sizes in Skype"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by Motorhead Kaze on 2009-02-14
Howdy. I tried out a couple tools to make Skype fonts appear larger yesterday, but there were no changes in the font sizes at all. Starting here: [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype) I followed the directions for the simple way, then slightly more involved way here: [https://help.ubuntu.com/community/QtGnome](https://help.ubuntu.com/community/QtGnome) (getting qtconfig) and finally, when these did nothing at all, I tried installing Kcontrol via the repos.

I followed all the directions to the letter, changed the font size in the respective gui and got jack.

This seems to be the official way to go, if there is one, but I have no idea why nothing has changed.

Please don't ask why I don't use Ekiga, or whatever. Skype is what I want, it does everything I want except that the fonts are 6pt or perhaps 8pt.

Suggestions on how to fix this would be appreciated!!

---

### Post by hansdown on 2009-02-14
Hi Motorhead Kaze.

Try using this link.

[http://www.skype.com/download/skype/linux/choose/?cm_mmc=google%252Flatsearch-_-NA-CA%257CEN-_-BD-_-kwid%253D200003805%257Ccreative%253D1035691106%257C-%257C100000000000000033961](http://www.skype.com/download/skype/linux/choose/?cm_mmc=google%252Flatsearch-_-NA-CA%257CEN-_-BD-_-kwid%253D200003805%257Ccreative%253D1035691106%257C-%257C100000000000000033961)

---

### Post by Motorhead Kaze on 2009-02-14
Hi again,

That is the link where I downloaded Skype from in the first place. Are you suggesting to reinstall?
...ok, I am back. I went ahead and removed Skype and reinstalled but the fonts are still tiny tiny. (no change)
I read somewhere a user talking about static vs. non-static Ubuntu and therefore the qtconfig did not work. Anyone know what that means? I have no idea if I have a static or non-static version...whatever. I have made no such choices.


PS. Hansdown: Vancouver rocks. Been there over 20 times. 
Friend from Seattle

---

### Post by Motorhead Kaze on 2009-02-14
FOUND IT!

I had tried qtconfig and it did not work. Read many, many Linux user forums and found that people who used the "Static version of Skype" were using **qt4-qtconfig** which I got from: [http://packages.ubuntu.com/hardy/qt4-qtconfig](http://packages.ubuntu.com/hardy/qt4-qtconfig) (for Hardy) At the bottom of the page you can choose to get the amd64 or i386 deb, and that link takes you to a list of actual links to the debian file depending upon your region.

Oddly, I could not figure out how to get it started in the terminal, and so I went to usr/bin and found the program and opened it from there. Changed the fonts and WHACKABAM (cool sound huh?) Skype responded on the fly. No restart required.

So, it may not be qtconfig, but qt4config that you want. Did me up fine.

Of course, if anybody knows how to start the program from terminal, or from applications, that would be swell.

Peace

PS where the heck did the "solved" button go?

---

### Post by hansdown on 2009-02-14
If you hit alt+f2 and type skype does it launch?

Glad you fixed the other problem.

The solved button and thanks button have been temporarily tuned off to reduce the load on the servers.

Take care.

---

### Post by Motorhead Kaze on 2009-02-17
Hi again Hansdown. Gosh you are a helpful person, thanks.

The problem turned out to be that the file name in usr/bin is "qtconfig-qt4" while the name is "qt4-qtconfig" when we download it. Like so:
```

sudo apt-get install qt4-qtconfig 

```
That is why I could not install with the terminal (I was typing [sudo apt-get install qtconfig-qt4]) and then once I got it, I was typing "qt4-qtconfig" into terminal or in "run"and it would not work. Very confusing. "They" should just choose 1 way to write the name. But hey, once I got it worked out, the program worked like a charm.

Thanks again!

---

### Post by hansdown on 2009-02-17
Glad you got it working Motorhead Kaze.

Good work.

---

