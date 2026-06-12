---
title: "Anti-aliasing in smaller Chinese fonts?"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by zipmon on 2011-04-24
Hi everyone!

Got my System76 Starling a few days ago and have been getting to know Ubuntu, my first Linux machine since a SuSEfied clamshell iBook back in the day! Everything's working great so far, except that Chinese fonts are incredibly jaggy and hard to read below a certain size. They look beautiful above 14 points, nice and smooth, but at 12 points and bellow they're hard to take! I've attached two screenshots, one of 12 point and one of 14 point Chinese to show what I mean. Hopefully someone will know the obvious solution I'm missing to make the smaller fonts smooth! 

I'm running Ubuntu 10.04 NBE.

Thanks a lot!!
-Morgan

---

### Post by mynameisnotbob on 2011-04-24
update your graphics drivers?

---

### Post by zipmon on 2011-04-24
I'm pretty sure I have the most up-to-date graphics drivers, and my western (non-Asian) fonts render fine and anti-aliased at very small sizes. It feels like there's a preference option somewhere I'm missing!

---

### Post by mynameisnotbob on 2011-04-24
Is hardware acceleration on?

---

### Post by zipmon on 2011-04-24
I'm not sure - how do I check? I do know, though, that the Visual Effects options under the Appearance preferences are greyed out, as in this picture:

---

### Post by mynameisnotbob on 2011-04-24
That just means you don have compiz. go to System->Administration->Additional Drivers.
Compiz might fix it. Put in terminal: ```
sudo apt-get install compiz
```.

---

### Post by zipmon on 2011-04-24
Wow - thanks for that, now I've got drop shadows and a much prettier desktop! Same problem with the Chinese fonts though - under 14 point they're blocky and not anti-aliased.

---

### Post by zipmon on 2011-04-25
Randomly browsing today, I found some evidence that it MUST be some setting somewhere, rather than an inability of my graphics card. Here's a screenshot of a Wikipedia article where one Japanese character (the first character in the second example) is anti-aliased (like I'd like all Asian fonts to be), and the rest are blocky. 

Any idea where I could fix this? Is there a font configuration file somewhere that says which fonts get anti-aliased and at what sizes?

---

### Post by mynameisnotbob on 2011-04-25
probably, but I dont know it. There might be a list of all ubuntu config files somewhere online, see if you can find it.

---

### Post by zipmon on 2011-04-25
I looked around and found references to making a .fonts.config file in the home directory, which I tried out a couple different options, but it only affects western fonts. I noticed too that when I tweak the font settings in the Appearance preferences tab with a window of Chinese text open in the background, all the Western text changes but the Asian text stays the same.

---

### Post by zipmon on 2011-04-25
OK - For anyone who's interested, I figured out a workaround!

-It's just a font issue - several of the fonts that are installed by default with the Chinese language support become ugly (to my eyes) bitmapped fonts at small sizes that don't anti-alias.

-My solution was to get rid of all those fonts. For the record, after installing Chinese language support on 10.04, that was everything included in the "metapackage for simplified Chinese" except for AR PL UKai. I removed the metapackage (language-support-fonts-zh-hans) in Ubuntu Software Center and then reinstalled the single package for AR PL UKai separately.

-Then I installed AR PL SungtiL GB from Ubuntu Software Center, because it seemed better suited as an all-purpose Chinese font than the only other one left after my purge, AR PL UKai (more brush style).

Now webpages with simplified Chinese all display beautifully, and SungtiL seems to be the default font whenever I use Chinese input.

Only one last holdout of weirdness - webpages with traditional Chinese characters use SungtiL for simplified characters and another font for traditional characters, even in the same sentence. I guess the hunt is on for a font that includes both Traditional and Simplified chars with no bitmapped versions at small sizes! :)

---

### Post by wt8008 on 2011-04-26
List the files you have in /etc/fonts/conf.d

Sometimes there are certain settings in there that default to non-AA Chinese fonts. I believe right now Ubuntu prefers Wen Quan Yi MicroHei as the default. In the past it used Wen Quan Yi ZenHei.

[http://wenq.org/enindex.cgi](http://wenq.org/enindex.cgi)

---

