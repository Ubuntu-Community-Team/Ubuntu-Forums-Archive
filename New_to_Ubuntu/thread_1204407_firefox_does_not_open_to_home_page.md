---
title: "firefox does not open to home page"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by chjo33 on 2009-07-04
[SIZE=4]I have set my home page in Preferences but when I open Firefox, it opens to the MS Bing page.  When I click on home button, same thing, doesn't go to set home page, opens Bing page.[/SIZE]

---

### Post by oldsoundguy on 2009-07-04
could it be your HOME PAGE got hacked with the B(L)ING search page? (what a piece of JUNK .. back to the days of porn sites showing up in the search again!!)

Try the url for your page .. if you get there THEN set it in preferences!

---

### Post by lovinglinux on 2009-07-04
Welcome to the forums.

See **Solution** [*[COLOR="Red"]**FOT003**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT003).

BTW, there is no need to use big letters on your posts.

---

### Post by chjo33 on 2009-07-06
> **oldsoundguy said:**
> could it be your HOME PAGE got hacked with the B(L)ING search page? (what a piece of JUNK .. back to the days of porn sites showing up in the search again!!)

Try the url for your page .. if you get there THEN set it in preferences!


As always I forget something.  I am running Ubuntu for netbooks on a EEE 900hd.
Tried it and doesn't work.  Typed in the URL, immediately goes to bing.com.

---

### Post by chjo33 on 2009-07-06
> **lovinglinux said:**
> Welcome to the forums.

See **Solution** [*[COLOR=Red]**FOT003**[/COLOR]*] from the Troubleshooting section of the [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT003").

BTW, there is no need to use big letters on your posts.

I am running Ubuntu lite for netbooks on a EEE 900hd.  I tried deleting the Places.sqlite file.  Restarted, Firefox still opens to Bing.com with home page preference set to something different.

---

### Post by wojox on 2009-07-06
Type about:config into address bar

Scroll down to browser.startup.homepage

See what it says.

If it's set to Bing double click it and put in the start page you want.

---

### Post by Mornedhel on 2009-07-06
> **chjo33 said:**
> Typed in the URL, immediately goes to bing.com.

Do you mean you are redirected to Bing every time you try to visit any URL ?

Sounds more like a DNS issue on your ISP's side to me, if that is indeed the case.

---

### Post by LowSky on 2009-07-06
what website are you trying to set as you homepage?

because Live.come now auto-directs to bing.com

---

### Post by lovinglinux on 2009-07-06
> **chjo33 said:**
> I am running Ubuntu lite for netbooks on a EEE 900hd.  I tried deleting the Places.sqlite file.  Restarted, Firefox still opens to Bing.com with home page preference set to something different.

Do you have more than one version of Firefox installed? If yes, then is it possible that you are using a profile from another folder, like ~/.mozilla/firefox-3.5.

Nevertheless, it could be a DNS issue or a redirection as already suggested above.

---

