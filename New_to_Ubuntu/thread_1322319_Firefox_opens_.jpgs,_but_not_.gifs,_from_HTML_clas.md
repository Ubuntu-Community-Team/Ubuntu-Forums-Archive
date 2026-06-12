---
title: "Firefox opens .jpgs, but not .gifs, from HTML class folder"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by Newbie-Doo on 2009-11-10
I am taking a beginning HTML class at my community college. Last week we did several exercises with HTML documents and .jpgs - those opened just fine in Firefox.

This week our images are .gifs, and they are not opening in Firefox.

I'm a newbie, happily using Ubuntu and trying to learn a few things as I go. (I'm pretty old for this.) My instructor is Windows-all-the-way, and has no patience with my open source inclinations. The work-load in the class is heavy, so I just don't have time for a lot of forum searching on this one. I can bail out and do this on my wife's Windows machine (The .gifs open just fine in her IE.), but I would rather not.

I hope there's some simple setting that I am missing that will let me continue in Ubuntu, so if anyone out there knows one, I would be obliged.

Thanks.

Newbie-Doo


Ubuntu/8.04 (hardy) Firefox/3.0.15
Dell Inspiron 530N desktop
Intel Pentium dual-core E2140 (1 MB L2, 1.60 GHz, 800 FSB)
1 GB Dual Channel DDR2 SDRAM at 667 MHz - 2DIMMs
128 MB NVIDIA GeForce 8300GS (Video Card)
250GB Serial ATA HD (7200RPM) w/ DataBurst Cache (Hard Drive)

---

### Post by amingv on 2009-11-10
Can you post some of the code you're using?
Also remember that under Unix/Linux filenames are case-sensitive, so the problem may be there, too.

---

### Post by jms1989 on 2009-11-10
check the permissions of the file, set it to world readable and see if that works. You can find it by right clicking on the files and choose properties and then the permissions tab. Also, try right-cling on it and select Open With > Mozilla Firefox and see if it loads that way. 

Hope this helps,
Cheers!

---

### Post by Newbie-Doo on 2009-11-10
> **amingv said:**
> Can you post some of the code you're using?
Also remember that under Unix/Linux filenames are case-sensitive, so the problem may be there, too.

Sure. Here is the exercise I'm working on now:

<html> 
<head> 
<title>Tia's Fan Page</title> 

<!--Newbie-Doo, Nov. 10, 2009-->

<style type="text/css">
h2 {
color: green;
font-style: italic; }
</style>
 
 
</head> 
 
<body> 
 
<p><img src="tialogo.gif" alt="image of Tia logo" height="60" width="517" /></p> 
 
<h2>The Latest Word on the New CD</h2> 
 
<p><em>The excitement keeps building.</em> We are now just days away from the release of Tia's new CD, the self-titled <em>Tia</em>, which will be released on <strong>January 25.</strong> Look for it in stores or order copies online. Available in stores right now is Tia's autobiography, <em>Tia &mdash; From Last to First.</em> Tia is embarking on an extensive promotional tour. She will make several television appearances to talk about herself, the new CD, and her autobiography.</p> 
 
<p>This spring, Tia will go on a cross-country concert tour in the United States. Dates and concert venues have not as yet been finalized, but they will be announced right here at Tia's Official Web site. Tia plans to tour every part of the country and perform in everything from small theatres to large arenas. <strong><em>Don't worry &mdash; you will get to see Tia!</em></strong></p> 
 
<p><img src="tia.gif" alt="photo of tia" height="250" width="300" /></p> 
 
<p>Below is a list of Tia's calendar of appearances and upcoming projects.</p> 
 
<h2>Calendar of Appearances</h2> 
<ol> 
  <li>January 5 &ndash; Interview and performance on Ellen</li> 
  <li>January 11 &ndash; Interview and performance on The Today Show</li> 
  <li>January 20 &ndash; Interview on the Letterman Show</li> 
  <li>January 25 &ndash; CD and book signing at the Virgin Music Store in Times Square</li> 
  <li>January 25 &ndash; Performance on MTV's TRL</li> 
</ol> 
 
<h2>Upcoming Projects</h2> 
<ul> 
  <li>CD and Book Promotion Tour in the <strong>United States, Mexico, and Europe</strong></li> 
  <li>Concert tour (U.S. only &ndash; dates and concert venues to be announced on March 23)</li> 
  <li>Co-starring role in a major Hollywood movie!</li> 
</ul> 
 
<h2>Breaking News &ndash;</h2> 
<p>Tia will sing a duet with rap star N70 on his upcoming new album, <em>Givin' Something Back.</em> The royalties from this album will be donated to more than a dozen inner-city charities. <em>More details to follow . . .</em></p> 
 
<p><img src="n70.gif" alt="picture of rap star N70" height="382" width="261" /></p> 
<h3>Rap Star N70</h3> 
 
</body> 
</html>

Was cut/paste the right way to do that? Anyway, we're working with assigned images and a pre-fab .htm file that we edit with a text editor. The image files are in the same folder, so I don't think it's a "browser can't find it" issue, is it?

Thanks for looking it over.

N-D

---

### Post by Newbie-Doo on 2009-11-10
> **jms1989 said:**
> check the permissions of the file, set it to world readable and see if that works. You can find it by right clicking on the files and choose properties and then the permissions tab. Also, try right-cling on it and select Open With > Mozilla Firefox and see if it loads that way. 

Hope this helps,
Cheers!

Thanks. I think I had already tried both of those things before I posted. Is "world readable" the same thing as Read permission for Owner, Group, and Others? (I don't see the specific wording, "world readable," in the Properties box.)

I had already hit Firefox Web Browser in the Open With tab.

Thanks.

N-D

---

### Post by dearingj on 2009-11-10
That HTML looks perfectly fine to me. Have you tried opening these images in another browser such as Opera or Epiphany?

---

### Post by amingv on 2009-11-10
Yeah, the code looks fine. In fact I just used it with some gifs in my computer and they all load fine in firefox. Did you check the files to see if there's any capitalized letter on their name?
Also, can you try opening the gif directly from firefox (In firefox go to File>Open File and try to open the gif from there.

---

### Post by jms1989 on 2009-11-11
> **Newbie-Doo said:**
> Thanks. I think I had already tried both of those things before I posted. Is "world readable" the same thing as Read permission for Owner, Group, and Others? (I don't see the specific wording, "world readable," in the Properties box.)

I had already hit Firefox Web Browser in the Open With tab.

Thanks.

N-D

Yes, I call it world readable because it can be read by anyone. -rw-r--r-- or 644.

After looking at your code it looks like you are calling the images from the same directory as the html page. Are the pictures in the same directory as you html page?

---

### Post by Newbie-Doo on 2009-11-11
> **amingv said:**
> Yeah, the code looks fine. In fact I just used it with some gifs in my computer and they all load fine in firefox. Did you check the files to see if there's any capitalized letter on their name?
Also, can you try opening the gif directly from firefox (In firefox go to File>Open File and try to open the gif from there.

That was what it was! I was so focused on the jpg/gif thing that I missed one of the first things I ever read about *NIX! (And I see that you had even mentioned it in your first post, too.)

Anyway, with a red face, I uncapitalized the image file names and they immediately opened in Firefox!

Thank you, amingv, and everyone else who helped me (re)learn a basic lesson!

Cheers,

Newbie-Doo

---

