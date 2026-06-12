---
title: "Need a web guru to help me with a couple of basics."
date: 2010-04-24
forum: New to Ubuntu
---

### Post by Kellemora on 2010-04-24
Hi Gang

Or more precisely, a shoulder to cry on and an ear to lend!

Here's the deal:
I'm old, but not to old to relearn and learn anew!

I have maintained my own HOME web pages now for years in Simple (now obsolete) HTML, but due to a medical condition, every so often I have to start over at ground zero and learn everything all over again.
I was shocked to see a few of my web pages still boast Win95 and Win98.

I thought I would hit the ground running and completely redo my web pages and bring them up to modern standards and eliminate all the "we don't do it that way anymore" methods.
Took a great refresher course in HTML, XHTML and am currently working on CSS and separate stylesheets, which is great!

Last week I thought I would advance a little further and study PHP.
Picked up several Tutorials and tried to do the lessons, to no avail, UNTIL some nice folks here on Ubuntu Forums informed me that I HAD to name my html pages, php AND install them in the /var/www directory.
Not a SINGLE tutorial I had said to do this, in any way that caught my attention, until after the fact, then I knew what they meant by putting it in my web folder.  In any case, this brought up having to install LAMP and getting my feet wet with that.

At this point I don't know if my ISP will let me make my HOME web pages as PHP.  But someone suggested I take a look at Javascript.
I have two GREAT tutorials that give step by step directions, except for one drawback.  They don't work!  I can open other peoples web sites using Javascript and they run just fine, so it's not a browser issue.  Javascript is activated.
But my thought here is, perhaps Javascript can only be used in a PHP web page OR it must have a different file extension OR it must be in a separate folder like PHP files.

Both of my lesson books, Page One, First Lesson start with simply
```

<html>
<body>
<script type="text/javascript">
{
document.write(<b>Hello World!</b>")
}
</body>
</html>

```

I've tried using the standard DOCTYPE headings as you would on a normal web page.  Everything I try works fine in html, and when I add CSS stylesheets external or internal, they work fine too.
But as I said, when I tried PHP, instead of Index.html I had to not only save it as Index.php, but HAD to put that document in the /var/www/directory.

OK, now I'm trying to do my lessons on JavaScript!

Does my html file need to be named something like Index.js?
Does it need to go in some special folder?
Does it need some supporting program associated with it?
I already know I can make EXTERNAL JavaScript pages named.js, like you do with filesfor.css

I spend hours practicing certain html codes and css codes to see what affects they do, and have learned how the background with forepages with curved corners and all that work.  Staying totally away from frames and an old habit of using tables as layout tools, CSS takes the place of all that.  But a couple of things I want to do seems that it can only be done with JavaScript and/or going the PHP route.

In any case, if I'm going to do my lessons from the JavaScript books, I need the pages that come BEFORE Page One Lesson One that tell me where and what to do with my Gedit file.  Which after messing around, now has red blocks all over the place, hi hi........

It's probably something simple like filename or location, that I don't about!  I do have Apache installed and can do my PHP lessons with no problems now!  Have all the elements of LAMP installed, not that I know anything about them yet.  Studying that too!

Thank you for any help you can give to me!

TTUL
Gary

---

### Post by -humanaut- on 2010-04-24
I'm not the greatest web coder in the world however if you're looking for something to run your code against (which is kind of what I picked up in your post) you could try downloading Quanta or one of the various other web development tools available in the repositories.

---

### Post by Kellemora on 2010-04-24
Thanks Humanaut

Don't think that's what I mean?

A web page is supposed to be viewable in a web browser!

I had to learn the hard way that if a web page is done in PHP, the file MUST be saved as .php in the /var/www directory and of course Apache installed.

Since I can't seem to see my JavaScript, I figured maybe it too needs some type of special file extension or a special location.
I haven't exhausted all the possibilities I can think of yet either.

Thanks

TTUL
Gary

---

### Post by Kellemora on 2010-04-24
This whole web site is done in JavaScript yet NOBODY knows How it done?

AMAZING!!!!!

---

### Post by achase79 on 2010-04-24
javascripting is called wrong.  This is what it should look like.
```
<html>
<body>
<script type="text/javascript">
document.write("<b>Hello World!</b>")
</script>
</body>
</html>
```

---

### Post by Kellemora on 2010-04-24
Thank you for your reply Achase!

I'm OVER my hurdle now!

My problem was, I was not told that JavaScript used in an html document had to be saved as a .php file within the /var/www directory!

These tutorials leave out the prerequisites required to get anything done.
Once you finally figure out what's wrong, THEN it works like a charm!

I'm already past the lessons on else if and playing with programming clocks.

Of course, I'll have to go back several times to retain any of it in a useful way.

A Tutorial NEEDS to start with TURN ON YOUR COMPUTER for olde geezers like myself.  I'm not quite THAT BAD, but you get my drift.

If I don't know WHAT a Fork looks like, how can I get one from the drawer it's hidden in back in the kitchen.
I need to be TOLD, Open TERMINAL, Sudo gedit, save file as PHP in /var/www else these lessons won't do diddly squat!!!!!

Thanks for lending an ear!

TTUL
Gary

---

