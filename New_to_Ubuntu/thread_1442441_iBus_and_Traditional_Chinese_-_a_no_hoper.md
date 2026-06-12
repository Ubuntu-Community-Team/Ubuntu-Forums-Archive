---
title: "iBus and Traditional Chinese - a no hoper?"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by eccomaggio on 2010-03-30
What's the current situation with iBus development? Is it just me or is the support for traditional chinese characters terrible? I live in Taiwan and it's a real deal-breaker for using linux. At best, I get mixed lists of traditional and simplified if I use one of the bewildering variety of pinyin input methods, most often i get the dreaded 'no input window'. 'bopomo' often just writes raw bopomo into the input line, rather than making it into characters. lots of programs don't even seem to accept iBus input.

I've googled 'linux ibus chinese' and read and digested the hits I got from this, and looked at the hits that 'ibus chinese' brought me on this forum, and nothing seems to improve the situation. The odd glitch would be fine, but iBus seems to be 98% glitch, and 2% hit.

What's going wrong? I'm using the package that comes with the distro and I've added support for traditional chinese. What have I done wrong? Is iBus fundamentally broken as far as non-mainland chinese goes?

A small additional point that may not be related - when I'm using iBus, the contents of the clipboard occasionally dump themselves at the cursor as I'm typing. Has anyone else noticed this? Like I said, it might not be related to iBus.

---

### Post by wenfuli on 2010-06-08
I can't actually help you, but I just wanted to tell you that I'm having the same problem. I just can't figure out how to get the actual characters to display.

---

### Post by expatCM on 2010-06-08
> and I've added support for traditional chinese. 

How did you do that?  Did you do this by first selecting the traditional Chinese language support and enabling fonts and iBus (System / Administration / Language Support)?  Or do you mean that you simply enabled support in the iBus preferences pages?

This link gives the general idea but you may have to slow down and think it through since this clip rushes through.
[http://www.youtube.com/watch?v=rvIobt5JpXI](http://www.youtube.com/watch?v=rvIobt5JpXI)

---

### Post by wenfuli on 2010-06-19
I've done everything that it is in the video many times. But I still can't get the actual characters to show on screen, all I get is the phonetic characters. For example, if try to type "strange" (because, well, this is strange), instead of the actual characters, I get: &#12561;&#12583;&#714;&#12557;&#12584;&#12574;&#715;. Please note, however, that Chinese does display fine. If I have a file, website, calendar item, contact, you name it, in Chinese, the characters display fine. I just can't type them. 

Once again, as the original poster stated, is the problem with traditional Chinese? The video shows simplified Chinese, and is using Pinyin as an input method. I -- and he -- want traditional Chinese, and I am using BoPoMoFo (&#12549;&#12550;&#12551;&#12552;) as the input method.

---

### Post by wenfuli on 2010-06-19
Sorry, just saw a reply in my earlier post and realised I was using the wrong input method. Everything works fine now.

Thanks to all who helped.

eccomaggio: Have you had any luck yet?

---

### Post by balkon on 2010-06-22
Yes, it seems traditional chinese  support in SCIM and IBus is terrible. My chinese friends who tried it can't imagine any chinese using Ubuntu.

How does Android and Apple (also linux or similar) do it ?

This what seems to be recommended: [http://www.youtube.com/watch?v=rvIobt5JpXI](http://www.youtube.com/watch?v=rvIobt5JpXI)
Activate "traditional chinese" in iBus, then choose in iBus your input method. We can choose &#12302;&#36895;&#25104;&#12303; or &#12302;&#36895;&#25104;&#19977;&#20195;.  But both are very bad. Quick (m17n) is even worse.

We also installed the package "scim-tables-zh" and "ibus-table-quick" which gives some extra bad choices. 

More info here: [http://wiki.ubuntu.hk/w/Install_Ubuntu_desktop#&#23433;&#35037;&#20489; &#38945;/&#36895;&#25104;&#36664;&#20837;&#27861;]("http://wiki.ubuntu.hk/w/Install_Ubuntu_desktop#%E5%AE%89%E8%A3%9D%E5%80%89%E9%A0%A1/%E9%80%9F%E6%88%90%E8%BC%B8%E5%85%A5%E6%B3%95")

We are still trying and experimenting. Please keep us informed about your progress.

I don't know where we can get help for this important issue. Would Canonical know there's a problem ?

I once heard of a professor in Hong Kong who made the table for the very good windows quick-package-tables. Should be easy to mutate them to linux.

Heeeee-eeelp !

---

### Post by wenfuli on 2010-06-22
balkan:

I'm having no problems with Traditional Chinese on my machine. My problems before were down to the input method I was using. Being in Taiwan where they use BoPoMoFo that's what I thought I needed, but an earlier poster suggested using Chewing and that has worked fine.

Where do you live? I'm pretty sure BoPoMoFo (&#12549;&#12550;&#12551;&#12552;) is only used in Taiwan, so if you're not living here, the problem might be down to your input method and not iBus. To reiterate, that's the problem I was having before. Once I changed the input method, I realised the problem was my input method and not iBus (or Ubuntu or Linux for that matter).

---

### Post by da burger on 2010-06-22
> **eccomaggio said:**
> A small additional point that may not be related - when I'm using iBus, the contents of the clipboard occasionally dump themselves at the cursor as I'm typing. Has anyone else noticed this? Like I said, it might not be related to iBus.
 
I'm afraid I can't help with your situation on chinese characters but I think I now what's causing this. It's a feature not a bug. If you hilight some text and middle click in a text buffer it will copy the text. It's much faster than usinng Ctrl-C Ctrl-V so just check you aren't clicking the middle button.

Also now I think of it, if you absolutely can't get the chinese characters to work consider filing a bug at launchpad. [www.launchpad.net](www.launchpad.net) I think a bug affecting an entire language pack will get a bit of attention (but I could be wrong).

Angus

---

### Post by balkon on 2010-06-23
@Wenfuli: I actually can't write or read much chinese, but my chinese friends that I'm trying to help know even less about computers.
We're in Hong Kong, so if you mean &#37239;&#38899; (Chewing) - &#26234;&#33021;&#27880;&#38899;&#36664;&#20837;&#27861;, then it's not usefull to us cantonese speakers because it uses pinyin.

---

### Post by wenfuli on 2010-06-23
@balkon:

I think I spelled your name wrong the first time! Sorry about that.

When talking about what they use here, I'm actually referring to &#27880;&#38899; (Zhuyin) and not Chewing, but Zhuyin is often referred to as BoPoMoFo when Romanised, so that was what I assumed I needed, but as I said, what I needed was Chewing. Everything seems the same between the two except that BoPoMoFo doesn't give me actual characters but Chewing does.

You are right, though, in that since you are in Hong Kong that neither one will work for you. Zhuyin and Pinyin are basically the same, the difference being that Pinyin uses Roman letters and Zhuyin uses symbols that are much like Chinese characters (and Zhuyin is much more accurate). In the end, both input methods require one to know how the character is pronounced in order to type it. I have no idea how people in Hong Kong type Chinese, but since you and I would be using the same characters but with different pronunciation (Mandarin vs. Cantonese), neither Zhuyin nor Pinyin would work for you. So I, at least, can't help you out, but wish I could.

---

### Post by balkon on 2010-06-25
My chinese friends like the cangjie on Android the most. It seems to be the standard in HK. [http://en.wikipedia.org/wiki/Cangjie_method](http://en.wikipedia.org/wiki/Cangjie_method)

But the standard one in Ubuntu is for sure very buggy. I found a lot of other versions on 
[http://packages.ubuntu.com](http://packages.ubuntu.com). They are easy to install :

[LIST]
[*][ibus-table-cns11643]("http://packages.ubuntu.com/ibus-table-cns11643")
[*][ibus-table-easy]("http://packages.ubuntu.com/ibus-table-easy")
[*][ibus-table-cantonhk]("http://packages.ubuntu.com/ibus-table-cantonhk")
[*][ibus-table-stroke5]("http://packages.ubuntu.com/ibus-table-stroke5")
[*][ibus-table-wu]("http://packages.ubuntu.com/ibus-table-wu")
[*][ibus-table-xinhua]("http://packages.ubuntu.com/ibus-table-xinhua")
[*][ibus-table-ziranma]("http://packages.ubuntu.com/ibus-table-ziranma")
[*][ibus-table-cangjie]("http://packages.ubuntu.com/ibus-table-cangjie")
[*][ibus-table-wubi]("http://packages.ubuntu.com/ibus-table-wubi")
[*][ibus-table-erbi]("http://packages.ubuntu.com/ibus-table-erbi")
[*][ibus-table-yong]("http://packages.ubuntu.com/ibus-table-yong")
[/LIST]
Can anybody try them ?

It's amazing how my chinese friends can almost find no information in chinese how to type cantonese on linux. Hong Kong chinese should be ashamed, or better, change to 26 characters: [http://en.wikipedia.org/wiki/Yale_Romanization](http://en.wikipedia.org/wiki/Yale_Romanization) . Chinese characters are just as clumsy as the US and UK metric systems.

---

### Post by kimikrishna on 2010-06-25
Hi,
I type my native language using SCIM .
You can try that too...

---

### Post by balkon on 2010-06-25
@kimikrishna: Thanks but iBus replaced SCIM in Ubuntu 9.10. It's like the new version of SCIM. We tried SCIM too. Cantonese with Scim is just as bad.

@Wenfuli: Thanks for trying to help.

---

### Post by smithintaiwan on 2010-10-26
&#26379;&#21451;&#20497;&#65292;

After not using Ubuntu for a few years, I‘ve just installed Ubuntu 10.10 and have to say that the new traditional Chinese support is much much improved. All you have to do is install iBus, select the standard pinyin and then click Ctrl-Shift F to toggle between simplified and traditional. 

After just a few minutes of testing, I would say that it's problematic, but definitely usable. It seems to have a few problems similar to Google Pinyin from about a year ago. For example, Taiwan can only be written as &#33274;&#28771;&#65292; not as &#21488;&#28771;&#12290; But the problem with &#32066;&#26044; is not present at all. Anyway, my point is, in answer to the initial "no hoper" question, we now have hope. I think this IME might actually work well.

Peace

Craig

---

### Post by tszkitc on 2010-10-27
Just solve the traditional chinese problem by remove Scim, IBUS and install GCIN.
You can do that by search in software center: gcin.

&#29992;&#20102;&#20043;&#24460;&#25171;&#27491;&#39636;&#23383;&#33298;&#26381;&#22810;&#20102;&#65292;&#25152;&#26377;&#23383;&#37117;&#25171;&#24471;&#20986;&#20358;&#12290;

&#20043;&#21069;&#25171;&#19981;&#20986;&#20358;&#30340;&#26377;&#65306;&#20491;&#12289;&#38283;&#12289;&#39636;&#31561;&#12290;

---

### Post by wencin on 2010-11-03
i also has a problem with the ibus cangjie input method (&#20489;&#38945;&#36664;&#20837;&#27861;), seems something has gone very wrong with the ibus table. even i cant type "&#20489;&#38945;&#36664;&#20837;&#27861;" by the cangjie input method itself! i've tried cangjie-m17n, cangjie3, cangjie5, cangjie-big - all cannot type certain characters.

example
&#20489; should be written by typing &#20154;&#25096;&#26085;&#21475; (oiar) but the ibus only shows &#20154;&#25096;&#26085;&#22899;(oiav) which will give &#39135;, if we try &#20154;&#25096;&#26085;&#21475;(oiar) and it will display &#39135;&#21475;

&#38945; should be written by typing &#22303;&#21475;&#19968;&#26376;&#37329;(grmbc), try &#22303;&#21475;&#19968;&#26376;&#37329;(grmbc) and it will display nothing

&#36664; should be written by typing &#21313;&#21313;&#20154;&#19968;&#24339;(jjomn), try &#21313;&#21313;&#20154;&#19968;&#24339;(jjomn) and it will display &#20094;&#19969;, because the ibus only has &#20094; &#65288;&#21313;&#21313;&#20154;&#24339; (jjon)&#65289; in it's table

other very common words i cannot type including

&#38272; should be written by typing &#26085;&#24339;, but the ibus will give &#20885;(&#26085;&#24339;&#26085;&#23665;). i also cannot type in the 'derivative' of &#38272; like &#38283; or &#38364;

&#38614; should be written by typing &#21475;&#25096;&#20154;&#22303;, but the ibus will give &#21769;&#22303;

this is very frustating. the cangjie input method works fine in 10.04, but become so messy after the upgrade.

@expatcm: i have done exactly what is in the video a lot of times too. this is not my first time installing language support, i've been using ubuntu since 7.04

---

### Post by wencin on 2010-11-05
> **tszkitc said:**
> Just solve the traditional chinese problem by remove Scim, IBUS and install GCIN.
You can do that by search in software center: gcin.

&#29992;&#20102;&#20043;&#24460;&#25171;&#27491;&#39636;&#23383;&#33298;&#26381;&#22810;&#20102;&#65292;&#25152;&#26377;&#23383;&#37117;&#25171;&#24471;&#20986;&#20358;&#12290;

&#20043;&#21069;&#25171;&#19981;&#20986;&#20358;&#30340;&#26377;&#65306;&#20491;&#12289;&#38283;&#12289;&#39636;&#31561;&#12290;


i've tried gcin and it works just fine! &#35613;&#35613;!

---

