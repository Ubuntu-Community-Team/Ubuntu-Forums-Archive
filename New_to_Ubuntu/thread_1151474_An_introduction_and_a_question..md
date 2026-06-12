---
title: "An introduction and a question."
date: 2009-05-07
forum: New to Ubuntu
---

### Post by NishiKotarou on 2009-05-07
Greetings everyone!

   I am a long time Vista user and recent Ubuntu convert (as of last night) and I must say I'm absolutely in love. So far I've personalised everything, fixed the issue of transfering files from my Ubuntu PC to my X-Box and found that there truly is a world of applications to meet my every whim. With all of that being said, I have finally found an issue I can't resolve and I am begging for your assistance.
   
I have successfully updated and utilised CompizConfig on my main user and am currently using the burn out and wobbly windows effects without a hitch. My problem lies in my additional users, I can't for the life of me get Visual Effects to activate. I did a lspci -v check on the main user and the additional users and they all state that I have Display controller: ATI Technologies Inc RV370 [Radeon X300SE]. So with that information in toe I know that both my main user and additional users recognise the fact I have a video card. I also made sure that I had the latest version of CompizConfig on my additional users so I'm completely at a loss. All help and suggestions GREATLY appreciated in advance.

Thanks,
Your friendly neighbourhood Ubuntu newbie

---

### Post by llamabr on 2009-05-07
Hi.  I don't know the answer to your question. But you'll be happy to know that ubuntu will run great on your xbox, when you're ready to take that next project on:

[http://www.xbox-linux.org/wiki/XUbuntu](http://www.xbox-linux.org/wiki/XUbuntu)

---

### Post by NishiKotarou on 2009-05-07
You know I had read something about people putting Ubuntu on their X-Box. It's something I'd really like to try, have you done it personally? I'm curious about the available functionalities and it's general stability. If it's just like the PC version then I can't say much else other than count me in!

---

### Post by Didius Falco on 2009-05-07
Hi Nishi,

Welcome to the Community!

I set up a new user, and logged in under that account, and I had access to Compiz  with the default permissions.

Have you changed the permissions of any other accounts you created?

Regards,

Didius

---

### Post by NishiKotarou on 2009-05-07
I actually made both of my additional users admins and gave them every permission in the book. I can access CompizConfig fine, select animations as well as extra animations, go in and select the desired transitions just like I do on my main user and then nada, zip, zilch! It was then that I checked whether Visual Effects were enabled and upon trying to change them to Extra it states that it can't do it on either of my additional users. Works just fine on the main, so it's just not making any sense to me. Thanks for the reply and to everyone who's helping!

---

### Post by Didius Falco on 2009-05-07
You could try adding fusion-icon to your setup (it's in the repositories) and using that to switch between compiz and metacity. It also has a "reload windows manager"option.

If no one here can help, you might have better luck at the Compiz forum:

[http://forum.compiz-fusion.org/](http://forum.compiz-fusion.org/)

Regards,

Didius

---

### Post by cjv8888 on 2009-05-07
Just a suggestion:

if you change user from your own log in page then the extra effects will not work.  You have to restart the computer and log in as the other user.

Did that help?

---

### Post by NishiKotarou on 2009-05-07
HAHA! CJV8888 you are a God! I can't believe how simple that was! I'm not really sure why it does that, but it does! I think being a Windows user for so long just makes you over think your problems. THANK YOU, THANK YOU, THANK YOU!

---

### Post by mcduck on 2009-05-07
> **NishiKotarou said:**
> HAHA! CJV8888 you are a God! I can't believe how simple that was! I'm not really sure why it does that, but it does! I think being a Windows user for so long just makes you over think your problems. THANK YOU, THANK YOU, THANK YOU!

The thing is that desktop effects requires using your graphic's cards direct rendering capabilities, which can only be used by one user at a time. If you log the first user out the second one is able to use the effects (no need to restart). If you just try to switch users (with the User Switcher-applet) the first user is still logged in and has the control of the graphics card.

---

### Post by NishiKotarou on 2009-05-07
Ah! That makes perfect sense. I was actually beginning to think Linux had a flaw for a minute lol. I still can't find one, it's frustrating. I just want a reason to hate this thing which seems all too wonderful.

---

### Post by Didius Falco on 2009-05-07
I learn some new things every day in here...Now if you'll excuse me, I have to beat that nugget of information into my brain. Hopefully, it'll displace something useless like the Brady Bunch theme song!

---

### Post by cjv8888 on 2009-05-07
> **NishiKotarou said:**
> HAHA! CJV8888 you are a God! I can't believe how simple that was! I'm not really sure why it does that, but it does! I think being a Windows user for so long just makes you over think your problems. THANK YOU, THANK YOU, THANK YOU!

LOL.  I was puzzling over the exact problem a year ago. Thought you might be doing the same thing.

Enjoy your Ubuntu !:)

---

