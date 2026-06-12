---
title: "Komposer not presenting webpage correctly on a MS Windows PC"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by a.v.l on 2009-07-28
I've been using Komposer for around eighteen months now and been quiet happy with it. Problem is, my only working computer is a Linux machine so I never gave it a thought that the presentation of a web site written in Linux may not appear correctly in MS Windows XP or Vista. BUT today I've had a look at my website on a windows laptop and it wasn't laid out correctly at all. Some fiddling around in Komposer made some difference but there are chunks of text which either appears to large or to small compared to how it looks on a Ubuntu PC....

Now I'm a little disappointed by this and I'm really beginning to wonder what is the point in using a Linux program when perhaps I would be better off using a Windows WYSIWYG software program which will likely be sure of presenting my website correctly for the majority, who are using Windows.

I really don't want to go back to Windows, does anyone have any suggestions please. Bear in mind that I do not have a good working knowledge of html ar anything else come to that to rely on and I am trying to use my website to attract business customers.
I could really do with some good advice please.

---

### Post by Terry of Astoria on 2009-07-28
What web page are you working on? There are tons of other ways to make a site than Kompozer. If you describe teh application (what kind of web site, and its purpose), someone may think of a solution for you. 
   You can use stuff like Content Management Systems (CMS) - eg: Joomla, Drupal, etc. - there are many. I like Wordpress - the one you install on your own server, [wordpress.org]("http://wordpress.org"). It's originally a blogging CMS but can be extended with plugins and cetera to be really versatile. The idea is that once a CMS is set up you simply log in and write or upload content a la facebook or so . . .

---

### Post by Jimleko211 on 2009-07-28
It might be because of the rendering engine.  If you used IE to test, try Firefox.

---

### Post by starcannon on 2009-07-28
My first thought is to run your page through the [W3C Validator]("http://validator.w3.org/"), correct any errors, and see if IE can render it correctly after that.
[http://validator.w3.org/](http://validator.w3.org/)
 
GL

---

### Post by a.v.l on 2009-07-29
> **Jimleko211 said:**
> It might be because of the rendering engine.  If you used IE to test, try Firefox.

When I view it in Firefox and it displays as written in Komposer.

---

### Post by ninjapirate89 on 2009-07-29
If you dont want to use a windows machine for testing purposes you can use browsershots.org to test what your page looks like in Internet Explorer and other browsers.

As for fixing the display errors that IE causes, use conditional statements for Internet Explorer. Here is a page explaining how they work.

[http://www.quirksmode.org/css/condcom.html](http://www.quirksmode.org/css/condcom.html)

---

### Post by ad_267 on 2009-07-29
Usually it's the browser rather than the operating system which is most important in how a webpage will look, although there can be variation between the same browser on a different OS.

This is a problem for all web developers and is due to the fact that different browsers render things differently. Internet Explorer is well known for not following web standards and breaking sites that work well in other browsers.

One thing to check is that your page isn't triggering quirks mode in IE: [http://en.wikipedia.org/wiki/Quirks_mode](http://en.wikipedia.org/wiki/Quirks_mode)

If you want you can post the web page here and someone will likely point out what you need to change.

---

### Post by a.v.l on 2009-07-29
> **starcannon said:**
> My first thought is to run your page through the [W3C Validator]("http://validator.w3.org/"), correct any errors, and see if IE can render it correctly after that.
[http://validator.w3.org/](http://validator.w3.org/)
 
GL

Thank you, I've run my URL though the validator and it came up with 36 errors. When I look for these in the designated line for example, Line 183, Column 4: I cannot see the error there. Can you confirm the meaning of  for example (line 183 and column)  actually means as it appears that I am looking  for the errors in the wrong place.

---

### Post by a.v.l on 2009-07-29
> **ninjapirate89 said:**
> If you dont want to use a windows machine for testing purposes you can use browsershots.org to test what your page looks like in Internet Explorer and other browsers.

As for fixing the display errors that IE causes, use conditional statements for Internet Explorer. Here is a page explaining how they work.

[http://www.quirksmode.org/css/condcom.html](http://www.quirksmode.org/css/condcom.html)

Many thanks for the browser checker it will be helpful.

---

### Post by Terry of Astoria on 2009-07-29
> **a.v.l said:**
> Thank you, I've run my URL though the validator and it came up with 36 errors. When I look for these in the designated line for example, Line 183, Column 4: I cannot see the error there. Can you confirm the meaning of  for example (line 183 and column)  actually means as it appears that I am looking  for the errors in the wrong place.
  It's showing you where it catches the error. Sometimes what you have to change is before or after the line indicated, but it often is right at the line. Often I have found that the first syntax error listed is very hard to find, but then next there's either a string of easy-to-find errors or sometimes a bunch of errors go away after I fix the first or second one . . . It just depends on what the error was in the first place. If I have accidentally left out a <ul> tag, for instance (starting an unordered list) then any <li> (list item) tags subsequent to that omission will throw an error. If I replace that <ul> tag, then all those errors will disappear with one stroke . . . So yes, it takes some care, but yes the validator will help find errors. Perhaps you'd care to reveal the url of your site? (It's perfectly OK if you don't, but it helps if we can see what you're working on . .)

---

### Post by a.v.l on 2009-07-29
> **Terry of Astoria said:**
> It's showing you where it catches the error. Sometimes what you have to change is before or after the line indicated, but it often is right at the line. Often I have found that the first syntax error listed is very hard to find, but then next there's either a string of easy-to-find errors or sometimes a bunch of errors go away after I fix the first or second one . . . It just depends on what the error was in the first place. If I have accidentally left out a <ul> tag, for instance (starting an unordered list) then any <li> (list item) tags subsequent to that omission will throw an error. If I replace that <ul> tag, then all those errors will disappear with one stroke . . . So yes, it takes some care, but yes the validator will help find errors. Perhaps you'd care to reveal the url of your site? (It's perfectly OK if you don't, but it helps if we can see what you're working on . .)

Thanks for that I'll take another look at it.

---

### Post by a.v.l on 2009-08-01
Because of "W3C Validator", I've been able to reduce my home webpage errors from 36 down to 3 but the remaining errors I'm unable to understand, can someone help please. These are the three errors what do they mean?

****************************************************
Line 94, Column 97: ID "TYPE_HERE" already defined

…small></span> <span class="c15" id="type_here"></span><span class="c15" id="t

&#9993;

An "id" is a unique identifier. Each time this attribute is used in a document it must have a different value. If you are using this attribute as a hook for style sheets it may be more appropriate to use classes (which group elements) than id (which are used to identify exactly one element).

****************************************************

Line 94, Column 137: ID "TYPE_HERE" already defined

…_here"></span><span class="c15" id="type_here"><small>built

&#9993;

An "id" is a unique identifier. Each time this attribute is used in a document it must have a different value. If you are using this attribute as a hook for style sheets it may be more appropriate to use classes (which group elements) than id (which are used to identify exactly one element).

******************************************************

Line 141, Column 54: ID "TYPE_HERE" already defined

<small class="c17"><br></small><span class="c15" id="Type_here"></span></td>

&#9993;

An "id" is a unique identifier. Each time this attribute is used in a document it must have a different value. If you are using this attribute as a hook for style sheets it may be more appropriate to use classes (which group elements) than id (which are used to identify exactly one element).

---

### Post by ad_267 on 2009-08-01
They mean exactly what they say.

The "id" attribute is supposed to be unique. You have multiple elements with the same id attribute.

---

