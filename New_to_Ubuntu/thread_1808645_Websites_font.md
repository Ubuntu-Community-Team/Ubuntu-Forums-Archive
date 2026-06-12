---
title: "Websites font"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by Dead root on 2011-07-20
Hello,

I read a small E-book about Ububtu and I got excited. So I installed it in a dual Boot with Windows 7. It's amazing, I thought Ubuntu is all about Command lines and things like that but I was shocked it was pretty easy and friendly to handle everything.

My main problem is I have few websites (French and Arabic) Unfortunately the font I have is totally different than the "font" I have on the website. Basically I see the site now in a different way. 

Is there a way to show the real "font" of the website? because I need to make posts but now I can't because what I see is different than what my users see. 

So I am using Windows 7 now to write posts..But I want to go back to Ubuntu...I've missed it :P

I hope you can help me.

Thanks !

---

### Post by mokrates on 2011-07-20
probably there is no 'real' font of the website. Windows (what browsers do you use under the respective systems?) probably just chooses a different font.

And what does 'totally different' mean? Does Ubuntu not display the arabic glyphs correctly, or does it just look different? 
What your users see is dependend on the fonts they're using also, so the problem most probably lies with the website, if the appearance is not just plain broken under ubuntu, and all your users continue to have the 'problem' you have, even if you fix it on your side.

---

### Post by Dead root on 2011-07-20
Hello,

No the site is fine. But what I see on Ububtu is totally on what I see from my windows machine. So I want to Know how can i have the same font so I can see the website in a good way?

---

### Post by no2498 on 2011-07-20
click view in/on your browser you can set things like style or encoding

---

### Post by mokrates on 2011-07-20
If he didn't mess up the settings in his browser, it shouldn't matter what's set in his settings.
The website should ask for the correct encoding and fonts, and the browser should automatically choose the right one.
If the browser shows 'something totally different' then the website doesn't give the browser enough hints to display it correctly OR there are fonts just missing (which would then mean, that every user of the site would have to install them)

So, i keep my opinion, it's the website, or he uses a weird browser (dunno, like glinks or dillo or sth.)

I would suggest you post 2 screenshots, one of how it should look like, and one how ubuntu displays it. And what browsers are you using?

---

### Post by amjjawad on 2011-07-20
> **mokrates said:**
> If he didn't mess up the settings in his browser, it shouldn't matter what's set in his settings.
The website should ask for the correct encoding and fonts, and the browser should automatically choose the right one.
If the browser shows 'something totally different' then the website doesn't give the browser enough hints to display it correctly OR there are fonts just missing (which would then mean, that every user of the site would have to install them)

So, i keep my opinion, it's the website, or he uses a weird browser (dunno, like glinks or dillo or sth.)

I would suggest you post 2 screenshots, one of how it should look like, and one how ubuntu displays it. And what browsers are you using?

Ubuntu does show different fonts than what Windows shows. 
The OP knows what he/she is talking about as I do have the same issue and I haven't messed up anything :)

I wish I could know how to do it!

Edit: I never use anything except Firefox and Chromium in Linux.

---

### Post by mokrates on 2011-07-20
If it's just different fonts and the website for some reason has to use standard windows fonts, try to install 'ttf-mscorefonts-installer'
(on a textconsole enter:
```
sudo apt-get install ttf-mscorefonts-installer
```
That gives you a set of standard windows fonts on your ubuntu, which can be used by your browsers.

About that screenshots: To make one, just press the 'printscreen' or 'print' key on your keyboard. Under ubuntu there should open a windows, which asks you where to save it, under windows, the screenshot (as i recall) goes to the clipboard, and you have to use some kind of graphics-application to save it.

---

### Post by Anuovis on 2011-07-20
It might depend on the browser you are using but at least Firefox can partly override the fonts (Preferences>Content>Advanced Fonts and Colors). The problem is that sometimes it doesn't or distorts the size, etc. Try and see if it makes any difference.

If Arabic texts are unreadable you might want to install the appropriate language support or look for a particular font to install that is easier on the eye.

Not sure if these can be an answer to your problem, a screenshot with comparison would really help to see it better.

---

### Post by Dead root on 2011-07-20
Hello guys.

Thanks for the updates. I installed Windows Font and now everything is working. I can see the same font again.

---

### Post by Dead root on 2011-07-20
> **amjjawad said:**
> Ubuntu does show different fonts than what Windows shows. 
The OP knows what he/she is talking about as I do have the same issue and I haven't messed up anything :)

I wish I could know how to do it!

Edit: I never use anything except Firefox and Chromium in Linux.
This how I fixed mine.

Download this file to your home : [http://www.box.net/shared/tvokeevkuk](http://www.box.net/shared/tvokeevkuk)

[COLOR=black]```
unzip Windows-Original-Fonts.zip
```

Then

```
[COLOR=black]mv Windows\ Fonts/ windows
```

then move it to font

```
[COLOR=black]sudo mv windows /usr/share/fonts/
```

Close and restart your firefox and you'll be be able to see the same font as Windows while browsing the Internet.
[/COLOR][/COLOR][/COLOR]

---

