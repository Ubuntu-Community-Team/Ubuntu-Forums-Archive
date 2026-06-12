---
title: "[SOLVED] How do you box your text in a post?"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by Lostin60's on 2009-01-07
I have noticed in many posts I see

Code:
|And then this text will be in a nice little box|

It really makes the code and the return easy to follow. I have tried various ways to do this, but none have worked.  I am gonna guess it is done with BBcode? Any and all help will be appreciated.  Oh, while I'm here I have one more question.  I am running Intrepid.  In the help manual it says that the command *sudo lshw -c network* will return information along with the words, CLAIMED, UNCLAIMED,ENABLED, and DISABLED, and it tells you what they mean. Much of the rest of the help information is given depending on which words you have. I have only ever gotten DISABLED, and that was only on my bridge connection. On the connections I needed to know about, there was nothing. This made it a bit difficult to follow the rest.  I ended up going to the end of the trouble shooting, and kind of reverse engineering the information. I figured it out(I'm here), but it was the long way around. Is this because the manual needs updating, is it that I am getting bad feedback from the command, or is it common and I am just missing something? Again, any and all help will be appreciated.
[COLOR="White"]aa[/COLOR]

---

### Post by whoop on 2009-01-07
"[code]"

and then again but with a "/" after the "[" (for the closing tag).
Put your text in between.

---

### Post by Paqman on 2009-01-07
> **Lostin60's said:**
> I am gonna guess it is done with BBcode?

Correct. The tags are [HTML]```

```[/HTML]

Or just hit the # button in the text editor.

---

### Post by Iowan on 2009-01-07
I use the "New Reply" button - the test entry box that pops up has a series of icons across the top.  If I have Java/JavaScript enabled, I can click on the "balloon" to generate a "quote" box, The # icon to generate a "code" box.  If I have a link to post, there's the globe-looking icon that asks for the link address.

>  In the help manual it says that the command *sudo lshw -c network* That'd be *sudo lshw -[COLOR="Red"]C[/COLOR] network*

---

### Post by Lostin60's on 2009-01-07
> **whoop said:**
> "[code]"

and then again but with a "/" after the "[" (for the closing tag).
Put your text in between.

As you can see, there is a bit more info in the quote than in the post.  I appreciate the help, but it all didn't make it into the post.

---

### Post by theozzlives on 2009-01-07
Hit the # button in the formatting bar  ```
and you get this
```

---

### Post by whoop on 2009-01-07
> **Lostin60's said:**
> As you can see, there is a bit more info in the quote than in the post.  I appreciate the help, but it all didn't make it into the post.

[html]```
some text
```[/html]

results in 
```
some text
```

I couldn't figure out how to put that in the message without getting it format into an actual quote :-) But now I got it.

---

### Post by Drubie on 2009-01-07
> Now you can quote important people too!
[indent] -Drubie[/indent]

---

### Post by Lostin60's on 2009-01-07
> **Paqman said:**
> Correct. The tags are [HTML]```

```[/HTML]

Or just hit the # button in the text editor.

Thanks Paqman. I googled BBcode for it, and could find nothing...hmmm. And I never would have thought about HTML at all, as the post box says HTML is off.

```
Yep, that works
```

And Iowan, I get the same return with -C as with -c

---

### Post by Lostin60's on 2009-01-07
> Now you can quote important people too! 

How 'bout that, Druibe?? I can!!  LOL And for those that feel, as I do, that the signature is too close to your text. At the end of your text, hit enter, then change font to white and type any letter, That give you one more space between lines
[COLOR="White"]a[/COLOR]

---

### Post by joshmuffin on 2009-01-07
> You can also quote things

By swapping the word CODE for QUOTE

---

### Post by Lostin60's on 2009-01-07
To all:
I appreciate everyone's help. I know that even a short help takes time.  I got Drubies answer first, so he got the "thanks", but the thanks are for all.
[COLOR="White"]a[/COLOR]

---

### Post by Drubie on 2009-01-07
Thanks for the thanks

I will remember to do add some white space to the bottom from now on!
[COLOR="White"]
blarg blarg blarg[/COLOR]  hehe, hidden messages!

---

### Post by bodhi.zazen on 2009-01-07
I should not tell you this but there are all kinds of code , it is called "[B]BB Code"

[/B]And what is worse, all the codes are posted in a hidden place

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

:lolflag:

And if you like that , try 

[http://ubuntuforums.org/misc.php?do=showsmilies](http://ubuntuforums.org/misc.php?do=showsmilies)

:guitar:

---

### Post by ugm6hr on 2009-01-07
> **Lostin60's said:**
> I have only ever gotten DISABLED, and that was only on my bridge connection. On the connections I needed to know about, there was nothing. This made it a bit difficult to follow the rest.  I ended up going to the end of the trouble shooting, and kind of reverse engineering the information. I figured it out(I'm here), but it was the long way around. Is this because the manual needs updating, is it that I am getting bad feedback from the command, or is it common and I am just missing something? 

lshw is a Linux code.  It *should* return details about your hardware and drivers etc.

-c should not work at all, while -class or -C will return details about a specific class of hardware (e.g. networking).

For more details, try:
```
man lshw
```

---

