---
title: "How much does lynx download compared to FF?"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by hayden92 on 2009-02-25
I started using lynx just for fun and decided that it is pretty cool. Recently I have been thinking about getting pre-paid mobile broadband but the cost for download/mb is pretty expensive.

My question was, how much download (on average, and approximately) will I save if I use lynx rather than firefox? 
Note: I have flashblock and noscript running with firefox.

My net surfing consists mainly of educational sites and Wikipedia along with the occasional ebay and sites like Naxos ([http://www.naxos.com/](http://www.naxos.com/))

Thanks,
Hayden

---

### Post by Metallion on 2009-02-25
I think you'll save quite a lot of download data with lynx since it downloads only text and no images etc. I personally don't know if I could live in an imageless internet though. :D

---

### Post by ModelM on 2009-02-25
Try it before you buy it. Just turn off images in Firefox & see how you like it.

---

### Post by hayden92 on 2009-02-25
Yes, I have turned off images and it damages the aesthetic appeal of web pages a bit, but it's nothing I can't handle.

I was just wondering if lynx saved much more download than firefox even if images are disabled.

---

### Post by Bearly Able on 2009-02-25
I've just finished building a simple Web site for a local B&B, and the finished thing comes in at 767KB.  Seven pages of HTML come in at 35KB, plus another 5KB for the style sheet.  That's a saving of around 727KB without the images, and this is a simple site; I imagine the average site will be even more image-intense.  Hope this helps.

---

### Post by RyanVanDiemen on 2009-02-25
Yes, the difference should be pretty big. I`m using Opera Mini on my mobile phone which downloads text from website and on top of that it changes the picture resolution to fit into mobile phone screen (it modifies the resolution so you don`t have to download too much data). I read on-line papers everyday when travelling to and from work and for the last 18 days I downloaded only something over 15 MB (remember this includes the pictures on web-sites). Since in lynx you won`t have any pictures, you should save even more data...

---

### Post by hayden92 on 2009-02-25
Thanks for the replies guys.
I do most of my browsing in lynx now but use FF when necessary.
Also, I downloaded the FF usage bar (shows current broadband usage, etc) so I will do a few of my own comparisons.

---

### Post by llamabr on 2009-02-25
Does lynx not download everything, or just not show everything?  I would think it would get the entire page, but only show the text bits.  You could easily test this, or ask at a lynx site.

You might also be interested in links, and links2, both text browsers, but a bit more feature rich.  Also w3m.

---

### Post by RyanVanDiemen on 2009-02-27
I don`t think it downloads all content and just shows readable information (text). Because as far as I know (it`s not much I have to admit) browser downloads html code and then it continues downloading other content. It knows where to find it from the information in html code. Lynx should only download html code and shouldn`t continue downloading pictures and flash if it doesn`t need it and is not able to show it anyway. Correct me somebody if my assumption is wrong.

---

### Post by llamabr on 2009-02-27
> **RyanVanDiemen said:**
> I don`t think it downloads all content and just shows readable information (text). Because as far as I know (it`s not much I have to admit) browser downloads html code and then it continues downloading other content. It knows where to find it from the information in html code. Lynx should only download html code and shouldn`t continue downloading pictures and flash if it doesn`t need it and is not able to show it anyway. Correct me somebody if my assumption is wrong.

That is a good point.  Again, this is easily testable, making it strange that we're trying to theorize about an empirical question.

---

### Post by thtrgremlin on 2009-02-27
@llamabr

It strictly gets exactly the page you requested, and does not get or follow any other content you don't ask it to. You can see this with pages that still use frames; I'll go to a page and it will pretty much just list the files that make up the frame as links, it does not go get the other pages.

Think of links as wget + parser. compare the output of these commands:

1. wget google.com -O - -q
2. lynx google.com --dump
3. wget google.com -O - -q | lynx --stdin

Also, if you are going to use lynx as your main web browser, getting familiar with its many options can be useful(man lynx).

---

### Post by llamabr on 2009-02-27
> **thtrgremlin said:**
> @llamabr


(man lynx).

This might strike some as good advice, but on this forum we are discouraged to recommend the reading of man pages to absolute beginners.

Please review the code of conduct, and keep this in mind.  Likewise with your sig.

---

### Post by hayden92 on 2009-02-27
Thanks thtrgremlin for the suggestion, I didn't think of reading the manual for lynx. Also, thanks to whoever suggested links2.

@ llamabr:
I'm not exactly a beginner (been using Ubuntu since 8.04) but I thought that my question was quite poor so it deserved to be in the AB section ;)

Hayden

---

### Post by Xiong Chiamiov on 2009-02-27
> **llamabr said:**
> This might strike some as good advice, but on this forum we are discouraged to recommend the reading of man pages to absolute beginners.

Please review the code of conduct, and keep this in mind.  Likewise with your sig.
Man pages are a great way of getting information.  They are often very terse, and perhaps difficult to understand, but oftentimes they have information that can't be found anywhere else.

---

