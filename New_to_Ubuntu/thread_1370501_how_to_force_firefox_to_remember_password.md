---
title: "how to force firefox to remember password"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by DarinB on 2010-01-02
i am using firefox 3.0.15 how can i force firefox to remember password,,,,i get the dialog box once then if you change your mind how do i get it back....i have some sites that will log on automatically from bookmarks other not? why is that?

---

### Post by Sidewinder1 on 2010-01-02
I have tried this as well to no avail; sometimes web sites show up in the "stored passwords" section, sometimes they don't, hopefully someone else has the answer...
Thread subscribed...

---

### Post by lovinglinux on 2010-01-02
> **DarinB said:**
> i am using firefox 3.0.15 how can i force firefox to remember password,,,,i get the dialog box once then if you change your mind how do i get it back....

Go to Firefox Preferences, then click the Security tab, then:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=142128&stc=1&d=1262454180[/IMG]

**[COLOR="Lime"]GREEN[/COLOR]** - to enable password remembering
**[COLOR="Blue"]BLUE[/COLOR]** -  to delete a password if you save the wrong one
**[COLOR="Red"]RED[/COLOR]** - to delete exceptions (sites that won't be remembered), so Firefox will ask again if you want to remember the password

> **DarinB said:**
> i have some sites that will log on automatically from bookmarks other not? why is that?

That has nothing to do with the bookmarks. They log in automatically because you have allowed persistent cookies. Nevertheless, there is a extension that can save bookmarks that automatically log in, even if you delete the cookies. See [Secure Login](https://addons.mozilla.org/en-US/firefox/addon/4429).

There are also extensions for integrating Firefox with Gnome and KDE password managers. See [KDE Wallet password integration](https://addons.mozilla.org/en-US/firefox/addon/49357)  and [Gnome-keyring password integration](https://addons.mozilla.org/en-US/firefox/addon/8737).

---

### Post by DarinB on 2010-01-02
thank you that got the prompt back but it still did not save my log in when i log in and save that page as a bookmark. I am thinking specifically of the linux questions forums, the Ubuntu forums allows for it so i am always a click away. with the other forums i have to go and add my log in each time a pain i don't mind with my bank i am used to that security but with the forums it silly.

---

### Post by lovinglinux on 2010-01-02
> **DarinB said:**
> thank you that got the prompt back but it still did not save my log in when i log in and save that page as a bookmark. I am thinking specifically of the linux questions forums, the Ubuntu forums allows for it so i am always a click away. with the other forums i have to go and add my log in each time a pain i don't mind with my bank i am used to that security but with the forums it silly.

See the Privacy tab. There is an option to control which sites will be allowed to save cookies. There is also an exception list, just like the one for passwords. If you allow the cookies for all sites, then you will be able to login automatically, without entering your password.

In regard to the need of typing the password, some sites (for example Windows Live) disable the auto fill functionality of Firefox and does not allow automatic login with cookies, so you have to type the password every time. This is really anoying, but is not Firefox fault.

As I said in my previous post, install Secure Login extension. You can login on sites with a single click or even with special bookmarks.

---

### Post by Captain_tux on 2010-01-02
Not all websites are configured to allow you to save your passwords... so it's neither an Ubuntu or Firefox issue, it's up to the website.

---

### Post by Sidewinder1 on 2010-01-03
Thank you all for the above! One thing that I've noticed that seems to help is that I don't bookmark a site unless and until I have already logged in. That seems, most of the time, to prevent me from having to login again.
HTH,
Side

---

### Post by DarinB on 2010-01-03
Hey Loving Linux, thanks I installed secure log in, It was a bit of a pain i had to manually all of my previously working book marks,,,,should i tick the box "activate Java script protection on log in????
I you a toaster lover? from caprica?

---

### Post by lovinglinux on 2010-01-03
> **DarinB said:**
> Hey Loving Linux, thanks I installed secure log in, It was a bit of a pain i had to manually all of my previously working book marks,,,,

Yep, that's a pain. I only use the Secure Login Bookmarks that I use on a daily basis and save them on Speed Dial.

> **DarinB said:**
> should i tick the box "activate Java script protection on log in????

Depends. I'm currently leaving it unchecked, because some sites do not play well with it. What you could do is check it and add to the exception list any site that fails to login or redirects you to the wrong page.

> **DarinB said:**
> I you a toaster lover? from caprica?

Yeah, I love the fraking toasters :) Best TV series ever! Can't wait to see Caprica series.

---

### Post by DarinB on 2010-01-03
I am waiting for a couple of the dvd's from the library. some of season 4 i couldn't find on line.
looking forward to seeing how the frak'in thing turns out.  i can't believe the frak'in skin jobs though, i wonder which ones are among up now, i bet bill gates is one! But its probably steve jobs!!!! Frak'in toasters.

---

### Post by DarinB on 2010-01-03
OK back to boring sh^t like log ins. I found that after adding Secure Login the sites that worked before stopped working after. i had to redo all of my bookmarks. Except ubuntu forums go figure???
not sure about the java thing i don't understand the benefit of it yet?

---

