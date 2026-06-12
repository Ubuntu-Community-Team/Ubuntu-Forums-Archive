---
title: "custom evolution signature double spaced"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by Carcharoth on 2011-05-18
In Thunderbird, I had a custom signature composed in HTML and saved as a file. Firefox reads it right, and so did Thunderbird. When I add it as a file to Evolution, it comes in double spaced. When I start from scratch with the editor supplied for the purpose in Evolution, I still get double spaced text. 

???

---

### Post by jtarin on 2011-05-18
Can you look at the source and not see how it is being formatted? Post the source here and let's look.
No further recommendations from here, as I just uninstalled Evolution 2 days ago after a year of using. I have found the client that comes with Seamonkey to be faster and more reliable.....I use IMAP with Gmail.

---

### Post by Carcharoth on 2011-05-19
been away overnight. the text I created by typing into the evolution text editor, I can find no way to copy. but here is the HTML file I created in gedit.

<!DOCTYPE html PUBLIC "-//W3C//DTD html 4.0 Transitional//EN">


<html>


<TITLE></TITLE>


<HEAD>

<STYLE></STYLE>

</head>


<body>

<hr>

<P ALIGN=RIGHT STYLE="margin-bottom: 0in"><FONT COLOR="#800000"><FONT FACE="Verdana, sans-serif"><FONT SIZE=2 STYLE="font-size: 11pt">

Roy Knapp<br /><br />

<b>Knapp Drafting &amp; Design</b><br />

<small>14450 N North Point Court<br />

Columbia, Missouri  65202<br /><br />

Office 573 442 6603<br />

Cell 573 999 9317</small><br /><br /> 

<i>roy@knappdesigns.net</i></FONT></FONT></FONT></P

</body>



</html>

IT LOOKS GOOD ELSEWHERE, but I am going to try taking out some break lines. maybe they are considered cariage returns in this world.

---

### Post by Carcharoth on 2011-05-19
AH HA! previous reply also double spaced.....
we may be on to something.

---

### Post by jtarin on 2011-05-19
I haven't done any HTML in awhile but what kind of tag is this...<br /> ? Looks like an XML tag.
And when did you need to have a start and ending <br> tag?

[http://www.w3schools.com/tags/tag_br.asp](http://www.w3schools.com/tags/tag_br.asp)

---

### Post by Phil Stone on 2011-05-19
Jtarin, Re HTML tags, (without confirming from the standards site W3C !!) this may be HTML 5 speak. Most tags now require the end slash to conform. The start tag you see is not a break it is **bold **for the text. I think the OP is creating formatting using direct HTML rather than css, of course these are both styles and should really be styled for rendering using css file. In this instance the double br's will create a double spaced break. Also notice the &ltn end tag for end 'P' is missing " > " which may case renderng issues.

Carcharoth - W3c schhools has a great validator to help with these lexical bugs, check the link in jtarins reply :)

---

### Post by jtarin on 2011-05-19
Your right on the "bold"....but <br /> is till not an html <br> tag. It could be suitable for XML content on a page somewhere, but we're talking about an email signature here......not rocket science. And "</P".....big problem......missed it. :)

---

### Post by Phil Stone on 2011-05-19
Yes you're right, looks like i need to brush up a bit too. Probably best to compare the standards for clarity heh. But instead I just had a little go at putting the style into css for Carcharoth. Its fairly basic but should be ok to play with.

hope this is good to get you going on with C :popcorn:

[HTML]
<!DOCTYPE html PUBLIC "-//W3C//DTD html 4.0 Transitional//EN">


<html>


<TITLE></TITLE>


<HEAD>

<STYLE>

body
{
margin-top:20px;
}

p
{
text-align:right;
margin: 0px;
padding: 0px;
font-family:Verdana, Sans-serif;
font-size:11pt;
color:#800000;
background-color:#badace; // delete this out once you have got the padding and margins right for you.
}
.rk
{
font-size:12pt;
margin-bottom: 10px;
}
.kdd
{
font-size:13pt;
font-style:bold;
margin-bottom:10px;
}
.add 
{
font-size:9pt;
}
.add2
{
margin: 0px 0px 10px 0px;
font-size:9pt;
}
.emadd
{
font-style:italic;
}

</STYLE>

</head>


<body>

<P class=rk>Roy Knapp</P>
<P class=kdd>Knapp Drafting &amp; Design</P>
<P class=add>14450 N North Point Court</P>
<P class=add2>Columbia, Missouri 65202</P>
<P class=add>Office 573 442 6603</P>
<P class=add2>Cell 573 999 9317</P>
<P class=emadd>roy@knappdesigns.net</P>

</body>



</html>
[/HTML]fraid this doesnt really help much with the orignal problem :(.
Well i guesss that'll teach me to answer the query huh - the html is 'cause its in thunderbird right and not for web page. doh!

---

### Post by Phil Stone on 2011-05-19
In all likelehood I'd imagine the problem is a setting in Evolution. Though it is odd that the double spacing occurs when you have copied it here. This is unlikely to be the <br> tags themselves being interpreted as a carriage return. I'm expecting you've had a trawl through the evolution settings?

---

### Post by Carcharoth on 2011-05-19
I have been through the Evolution settings and found no joy (yet).
What your HTML code shows in my Evolution ( as set presently ) is this:

file:///home/roy/Desktop/Screenshot.png

uncertain if the image will be included in post.
the spacing is double, the text is left aligned, and the font size is constant.

when I open your file with Firefox, I get the formatting we all desire.
which is just what happens with my version.

something in the Evolution settings I think (too).

I continue to play with it.

---

### Post by Phil Stone on 2011-05-20
Carcharoth,

Yes I'm afraid my solution previously was based on the assumption that this was being used for web reproduction as clearly did not read the query. I think seeing all those <br />'s sidetracked me.

I have tried a few different variations of writing the html. I even got to some very unorthodox coding solutions but the problem is not the code or carriage returns being erroneously input into the files when the composer saves the signature. (The preview is fine it's just when the signature is written to file)

I think the problem is one of scale - when you switch between the text and html modes the resolution for the html mode seems to drop resulting in a large rendering of html.

There are  possible workarounds I can see.

 1. add a script to generate the signature - problem being what script, language and what peramaters are to be used?

 2. create an image file which you can then add in to the HTML mode of the signature maker. The only drawback with this is if the recipient does not access images via their e-mail.

3. Use the text mode.

here's some useless pre code which tried out.

```

<hr>
<div align="right">
<pre><font size="3" face="verdana, sans-serif" color="#800000">
Roy Knapp</font>
<font size="4" face="verdana, sans-serif" color="#800000"><b>
Knapp Drafting &amp; Design</b></font>
<font size="2" face="verdana, sans-serif" color="#800000">
14450 N North Point Court
Columbia, Missouri 65202
Office 573 442 6603
Cell 573 999 9317
<i>
roy@knappdesigns.net
</i></font>
</pre>
</div>


```It may be worth submitting a bug report via the help drop-down - after seeing if this is a known problem at the project site first of course. It looks as though there's a lot of general updating and fixes going on so it may be that this is under their attention already.

---

### Post by Phil Stone on 2011-05-20
Carcharoth,

I have just noticed three is another option on the HTML signature maker. It's a little bit temperamental but you may be able to get it do what you like after a bit of persuading.

If you select table insert and then you can set the table rows to 10 and columns to 1 etc...
Not sure if you will be able to copy in formatted text eg verdana at certain size, it seems to not enjoy having difernt size fonts on lines unless they are headers. But the double spacing is not occuring betwen the lines of the address and phone numbers.

Once the table is set you can then right click > properties and switch the borders off. This might be the result.

Phil

---

### Post by forliberty on 2012-01-25
Not sure if this helps, but I had a similar, but simpler problem and Googling turned up this thread. I was just trying to create my own HTML signature using Evolution's signature editor and found Evolution was double-spacing the entire signature. To find the problem, I created the simplest possible signature with two lines of text. Evolution interpreted it as single-spaced. Then I centered the two lines of text. Suddenly, it appeared as double-spaced. To fix the problem, I edited the signature file with gedit. The signature files can be found at /home/[your user]/.evolution/signatures. The Evolution-created file looked like this: 

<DIV ALIGN=center>San Diego, California 92127</DIV>
<BR>
<DIV ALIGN=center>Telephone:&nbsp; 858-592-6250; Fax: 858-451-3643</DIV>
<BR>

I changed it by removing the <BR> codes, and voila, single-spaced lines!

---

