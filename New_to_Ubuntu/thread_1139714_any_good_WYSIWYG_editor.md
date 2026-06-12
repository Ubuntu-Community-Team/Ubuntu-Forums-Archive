---
title: "any good WYSIWYG editor ??"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by Sweet Sniff on 2009-04-27
Hello guys,

first of all thank you for your help in advance, I have been reading this forum for a long time and I have learned a lot here. This is my first time to ask for help coz I'm really desperate now

I have searched this forum for a long time trying to answer this question but with no luck...

I have read this topic
[http://ubuntuforums.org/showthread.php?t=1135712](http://ubuntuforums.org/showthread.php?t=1135712)

and many similar ones, but everybody seems to have the same solutions that does not fit my needs...

I'm looking for a WYSIWYG editor that support right-to-left languages like Arabic and Hebrew ... that's all what I need

somethings that you should NOT tell me :

1- learn how to code in HTML : I'm already a professional in HTML and as a matter of fact I teach HTML, XHTML, XML , CSS and PHP in college. I need something to do the work fast that's it.

2- use nvu or Kompozer : they are the most buggy softwares that I ever used, they keep crashing every time I go to the menues

3- use Amaya: it does not support right-to-left languages


Since I get tired of trying different softwares, any help is highly appreciated and I will try any other software u tell me about


Best Regards,

---

### Post by dyrer on 2009-04-27
Try Aptana and Geany

---

### Post by Sweet Sniff on 2009-04-27
> **dyrer said:**
> Try Aptana and Geany
thanks dyrer for the fast respond

Geany is a text editor but it seems to be very good that i may use it instead of screem

I will try Aptana and I will come back with the results

Best Regards,

---

### Post by 3rdalbum on 2009-04-27
Have you tried the Composer section of Seamonkey? (it's installed along with the browser). It's the program that Nvu and Kompozer are based on, but without the menu crashing problem.

---

### Post by Sweet Sniff on 2009-04-27
> **Sweet Sniff said:**
> thanks dyrer for the fast respond

Geany is a text editor but it seems to be very good that i may use it instead of screem

I will try Aptana and I will come back with the results

Best Regards,
I did not managed to install Aptana

I have followed the instructions in that blog :
[http://jasonleveille.com/2008/05/installing-aptana-on-ubuntu-804/](http://jasonleveille.com/2008/05/installing-aptana-on-ubuntu-804/)

but I got stuck at step#7
I got the error message : 
bash: firefox-2: command not found

when I try to lunch Aptana now I get the following error message :
An error has occurred. See the log file
/home/sweetsniff/Aptana Studio/.metadata/.log

I have uploaded my error log since it is too big to be here :
[http://sweetsniff.com/files/aptana.log](http://sweetsniff.com/files/aptana.log)


any idea ?

---

### Post by Sweet Sniff on 2009-04-27
> **3rdalbum said:**
> Have you tried the Composer section of Seamonkey? (it's installed along with the browser). It's the program that Nvu and Kompozer are based on, but without the menu crashing problem.
thanks for your suggestions I will try that too and come back with the result

---

### Post by Sweet Sniff on 2009-04-27
> **3rdalbum said:**
> Have you tried the Composer section of Seamonkey? (it's installed along with the browser). It's the program that Nvu and Kompozer are based on, but without the menu crashing problem.
seamonkey does not seem support right to left languages, but it is the best I have tried so far

thank again for the suggestion

Best Regards,

---

### Post by Sweet Sniff on 2009-04-27
any other good suggestions...

anybody knows a lightweight WYSIWYG editor in windows that support left-to-right languages that I can use with WINE

I was a mac user and I don't really know about Windows apps

in mac I was using Adobe Dreamwaver, but I only have Ubuntu now

Best Regards,

---

### Post by ssdt on 2009-04-27
TinyMCE is a good one for that.

---

### Post by Captain Legless on 2009-04-27
I use the Windoze version of Dreamweaver installed via WINE. It seems to work OK for me.

---

### Post by Johnsie on 2009-04-27
Frontpage express works in wine too... but then you might as well be using Windwws.

---

### Post by Najmudin on 2009-04-27
> **Captain Legless said:**
> I use the Windoze version of Dreamweaver installed via WINE. It seems to work OK for me.

That's right,it works will with wine.

---

### Post by Sweet Sniff on 2009-04-27
> **ssdt said:**
> TinyMCE is a good one for that.
thanks for the suggestion I will try that one too

---

### Post by Sweet Sniff on 2009-04-27
> **Captain Legless said:**
> I use the Windoze version of Dreamweaver installed via WINE. It seems to work OK for me.
that's interesting

I have a license for Adobe Creative Suite 3 for mac

I will see if I can transfer my license to Windoz so I can open it in WINE


Linux is such a huge community that believes in open source, why there is no good WYSIWYG editor out there??

to answer my question -> I think the open source community does not believe in rapid development

if I'm talking as a software developer, I really enjoy working directly with the code and I like the freedom in that approach.

but, if I'm a company, time is money and I don't have time to satisfy my enjoyment

Best Regards,

---

### Post by freshT on 2009-04-27
Good luck with Aptana, I can't get it to work!

---

### Post by JC Cheloven on 2009-04-28
Most likely Kompozer crashes for you due to a known problem (different GTK versions in ubuntu and kompozer). 

But I've found this simple workaround:

-> Download from the main site [http://www.kompozer.net/download.php](http://www.kompozer.net/download.php) the .tar.gz (not the .deb or whatever).

-> Uncompress it in a directory of your choice

-> From nautilus (or by any means) execute the shell script named "kompozer".

You have kompozer running without the need of even installing it. I've using it this way for several months in intrepid with no problem at all. The particular file I downloaded is kompozer-20090206.tar.gz . A newer one should also do fine, I suppose.

Note: I didn't try on jaunty though.

---

### Post by shane2peru on 2009-05-21
In my endless search for a good wysiwyg web page builder, I have once again searched for this on the forums, and once again disappointed and the lack of good answers.  I'm downloading the latest Kompozer (unstable - not supposed to be used in production) because of the ever existing problem of Kompozer in Ubuntu.  I'm really tempted to buy Dreamweaver and install it via wine because I really need something of this effect.  

@Sweet Sniff - Check out Bluefish (it is in the repos) for direct html editing I really like it, I use it for a lot of things.  Enjoy.

Shane

---

### Post by fluxlizard on 2009-05-21
I'll second bluefish. I use it all the time.

After creating and maintaining a site for about 18 months now with frontpage I have a very negative opinion of that software. It barfs trash all over the code, and being particular about layout, it can be frustrating to use- I end up going in and editing the code to fix things constantly anyway. And I hate how it fakes includes instead of making them server side.

 For that matter, I haven't been very impressed with any wysiwyg software. I still haven't tried dreamweaver though...

---

### Post by shane2peru on 2009-05-21
Ohh, that hurt!  I just saw the price for Dream weaver, I don't even shovel out that much for my OS! lol  :D  No way am I paying that much for software, I'm not making money off my web sites, perhaps if I was, I would think about it.  I had a second thought.  OpenOffice does edit web sites too, I can't say how good it is or isn't all I know is I have done it before in the past.  Just a thought.

Shane

---

### Post by ashmew2 on 2009-05-21
+1 to bluefish.

Not really helping :

I think the Forums also offer a WYSIWYG for replying to threads and stuff ;)

---

