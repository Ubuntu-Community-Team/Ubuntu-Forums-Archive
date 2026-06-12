---
title: "Typing Chinese"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by wenfuli on 2010-06-08
I'm trying to figure out how to type Chinese with Ubuntu. I've found instructions on how to do so with Ubuntu versions up to 8, but not for the 10.04 version I'm using. I have install SCIM and the language packs, I believe. I've gone into SCIM and played around in there, I just can't get the the input method to change to Chinese.

One problem could be is that all the support I have seen regarding Chinese is dealing with typing using pinyin. I need to type using zhuyin.

Any help would be appreciated.

---

### Post by expatCM on 2010-06-08
You do not need scim with 10.04 ....  everything changed.

You need to enable Chinese language support (System / Administration / Language Support) and then use iBus (System / Preferences / iBus).

In iBus you will find a lot to play with .......  but it works very well indeed.

---

### Post by wenfuli on 2010-06-08
Thanks for the help. However, it doesn't quite work. When I try typing Chinese, all I get is the phonetic symbols, but no actual characters. For example, when I try to type the Chinese for "I want to be able to type in Chinese," I get this: "&#12584;&#12571;&#711;&#12583;&#12576;&#715;&#12555;&#12581;&#714;&#12557;&#12577;&#715;&#12553;&#12570;&#711;&#12563;&#12584;&#12581;&#714;&#12584;&#12579;&#714;&#12567;&#715;". So how do I get the actual characters to display?

---

### Post by expatCM on 2010-06-08
It works on my machine so what is the difference between us ....

You did install the Chinese Language Support?  Did you install any fonts?  Did you check the iBus box on the language support page?

---

### Post by wenfuli on 2010-06-08
Never thought of installing fonts....I just installed one font but nothing has changed. I'll try installing more. Are there any fonts you would recommend I install?
You are using traditional characters, no, and not simplified ones? The implication I got from someone else's thread who is having the same problem I am is that inputting Chinese is fine if you're using simplified characters but doesn't quite work with traditional ones.

---

### Post by expatCM on 2010-06-08
I posted this link on another thread.  Perhaps it will help you.  It runs very quickly though so you may want to think about what you have seen and then compare ....
[http://www.youtube.com/watch?v=rvIobt5JpXI](http://www.youtube.com/watch?v=rvIobt5JpXI)

There are Chinese fonts to be found in Synaptic.  Google will also deliver a range of free Chinese fonts but .... quite frankly you probably need only what is installed by default and perhaps a few others from Synaptic.

---

### Post by truker on 2010-06-09
Thanks... the iBus method worked. I don't know why Ubuntu doesn't make it easier or more obvious...

As a note, if you're looking for Zhu-Ying (&#27880;&#38899;), don't pick "Chinese-bopomofo" as the input method. Use "Chinese-Chewing".

---

### Post by wenfuli on 2010-06-19
truker:

Thanks, using "Chewing" worked. I can now type in Chinese (&#25105;&#32066;&#26044;&#21487;&#20197;&#25171;&#20013;&#25991;&#20102;&#65281;)

---

