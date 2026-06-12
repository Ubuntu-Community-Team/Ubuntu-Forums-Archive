---
title: "Writing Stylish Styles"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by RealG187 on 2009-11-13
I am trying to write a style for a site I goto. [http://psphomebrew.net](http://psphomebrew.net)
Sign
Here is what I got:
```
@namespace url(http://www.w3.org/1999/xhtml);

@-moz-document domain("psphomebrew.net") {

}
body {background-image:none !important; background-color:#262626 !important;}
```
So I changed the background of the site. But how do I change the background where the sections are. For example under "Emulators (New Line) PSP emulators" it's still gray and for firmware it's still white.

Also it changes replaces the background on all sites, how do I make it just do the one for this site?

---

### Post by tjwoosta on 2009-11-14
Its working for all sites instead of that particular site because you put the end bracket before the code.  It should be like this

```

@namespace url(http://www.w3.org/1999/xhtml);

@-moz-document domain("psphomebrew.net") {


body {background-image:none !important; background-color:#262626 !important;}

}

```

Notice theres a begin bracket at the end of the @-moz-document line. That is the start of your code, where the end bracket is the end of your code. All of your setting should be between those two brackets.

The easiest way to apply the code to the entire page rather then only the body would be to just use * instead. (this symbol basically means all)

```

@namespace url(http://www.w3.org/1999/xhtml);

@-moz-document domain("psphomebrew.net") {


* {background-image:none !important; background-color:#262626 !important;}

}

```

Another way would be to use firebug and just right click the section your interested in and find out what the id or class of that section is and call on it seperately. example ..

```

@namespace url(http://www.w3.org/1999/xhtml);

@-moz-document domain("psphomebrew.net") {


body {background-image:none !important; background-color:#262626 !important;}

.tHeading {background-image:none !important; background-color:#262626 !important;}

}

```

As for the table, I still don't fully understand how to style tables. One method would be to use td followed by the class for that section of the table example..

```

@namespace url(http://www.w3.org/1999/xhtml);

@-moz-document domain("psphomebrew.net") {


body {background-image:none !important; background-color:#262626 !important;}

td .text {background-image:none !important; background-color:#3e3e3e !important;}

td .smText {background-image:none !important; background-color:#3e3e3e !important;}


}

```

---

### Post by RealG187 on 2009-11-14
So the background for "Emulators" is grey and "Firmware" is white. When I try coding the style they both appear the same color. How can I make it alternate like that?

And how do you change text color?

---

### Post by tjwoosta on 2009-11-14
> So the background for "Emulators" is grey and "Firmware" is white. When I try coding the style they both appear the same color. How can I make it alternate like that?

Thats where I get lost myself. I still havn't figured that one out. Maybe someone with more CSS knowledge can help you out. Theres a great forum with plently of CSS experts here
[http://forums.devshed.com/css-help-116/](http://forums.devshed.com/css-help-116/)

> And how do you change text color? 

For text you can just use color: #9a9a9a (or whatever color). So for example if you want to change the text color for everything you could use

```

* {
color: #9a9a9a !important;
}

```

---

### Post by RealG187 on 2009-11-15
Another problem I am having is when I change the hexadeciaml number is one part of the code two parts of the page change color.

See the attachment, when I change the code the two parts of the page I made red arrows to change. I want the background behing the logo with the red PSP and the background color under the firmware section to be different.

I want the firmware part to stay black, but on the logo it's black making an awkward block box on the upper left of the site, when I try to change it to the dark blueish green (002222 I think it was) the other part changed too.

I think they both use class=nav

---

### Post by tjwoosta on 2009-11-15
hmm... thats weird


What I would probably do here, that would probably be easier anyway, is just look over the already implemented css and just call on all the same objects they did but use your own settings.

here is the css for psphomebrew.net

```

.text {
	font-family: Tahoma, Verdana, Arial, Helvetica, sans-serif;
	color : #000000;
	font-size: 12px;
	font-weight: normal;

}

.error {
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	color : #FF0000;
	font-size: 13px;
	font-weight: normal;
}

.tiText {
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	color : #000000;
	font-size: 11px;
	font-weight: normal;
}

.bold {
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	color : #000000;
	font-size: 13px;
	font-weight: bold;
}

.smText {
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	color : #000000;
	font-size: 10px;
	font-weight: normal;
}

.heading {
	font-family: tahoma, Arial, Helvetica, sans-serif;
	color : #000000;
	font-size: 24px;
	font-weight: bold;
}

.lgText {

	font-family: tahoma, Arial, Helvetica, sans-serif; 
	font-size: 15px; 
	color: #000000; 
	font-weight: bold;
}

.tHeading {
	font-family: tahoma, Arial, Helvetica, sans-serif; 
	font-size: 12px; 
	color: #FFFFFF; 
	font-weight: bold;
}

.tiHeading {
	font-family: tahoma, Arial, Helvetica, sans-serif; 
	font-size: 12px; 
	color: #333333; 
	font-weight: bold;
}

.highlight {
	background-color: #ffff66
}

a  {
		color : #333333;
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration: none;
	font-size: 14px;
	font-weight: bold;

}

a:hover {
			color : #333333;
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration: none;
	font-size: 14px;
	font-weight: underline;
}

a:visited {
			color : #333333;
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration: none;
	font-size: 14px;
	font-weight: bold;	
}

a:visited:hover {
			color : #333333;
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration: none;
	font-size: 14px;
	font-weight: underline;
}

a.boldLink:hover {
	color : #FF0000;
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration : underline;
	font-size: 13px;
	font-weight: bold;
}

a.boldLink  {
	color : #000000;
	font-family: Tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration: underline;
	font-size: 16px;
	font-weight: bold;
}

.boldLink a {
	color : #000000;
	font-family: Tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration: underline;
	font-size: 16px;
	font-weight: bold;
}


a.boldLink:visited {
	color : #990099;
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration : underline;
	font-size: 13px;
	font-weight: bold;
}

a.boldLink:visited:hover {
	color : #FF0000;
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration : underline;
	font-size: 13px;
	font-weight: bold;
}

a.smLink  {
	color : #000000;
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration: underline;
	font-size: 11px;
	font-weight: normal;
}

a.smLink:hover {
	color : #000000;
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration : underline;
	font-size: 11px;
	font-weight: normal;
}

a.smLink:visited  {
	color : #000000;
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration: underline;
	font-size: 11px;
	font-weight: normal;
}

a.smLink:visited:hover {
	color : #000000;
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration : underline;
	font-size: 11px;
	font-weight: normal;
}


nav  {
	color : #000000;
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration: none;
	font-size: 11px;
	font-weight: bold;
	padding-left:5px;
}


.nav a  {
	color : #000000;
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration: none;
	font-size: 11px;
	font-weight: bold;
	padding-left:5px;
}

a.nav  {
	color : #000000;
	font-family: Tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration: none;
	font-size: 11px;
	font-weight: bold;
	padding-left:5px;
}


a.nav:hover {
	color : #000000;
	font-family: Tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration : underline;
	font-size: 11px;
	font-weight: bold;
	padding-left:5px;
}

a.nav:visited {
	color : #000000;
	font-family: Tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration : none;
	font-size: 11px;
	font-weight: bold;
	padding-left:5px;
}

a.nav:visited:hover {
	color : #000000;
	font-family: Tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration : underline;
	font-size: 11px;
	font-weight: bold;
	padding-left:5px;
}


a.npLink  {
	color : #000000;
	font-family: Tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration: none;
	font-size: 11px;
	font-weight: bold;
}


a.npLink:hover {
	color : #000000;
	font-family: Tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration : underline;
	font-size: 11px;
	font-weight: bold;
}

a.npLink:visited {
	color : #000000;
	font-family: Tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration : none;
	font-size: 11px;
	font-weight: bold;
}

a.npLink:visited:hover {
	color : #000000;
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration : underline;
	font-size: 11px;
	font-weight: bold;
}

a.cat  {
	color : #000000;
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration: none;
	font-size: 12px;
	font-weight: bold;
}


a.cat:hover {
	color : #000000;
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration : underline;
	font-size: 12px;
	font-weight: bold;
}

a.cat:visited {
	color : #000000;
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration : none;
	font-size: 12px;
	font-weight: bold;
}

a.cat:visited:hover {
	color : #000000;
	font-family: tahoma, Verdana, Arial, Helvetica, sans-serif;
	text-decoration : underline;
	font-size: 12px;
	font-weight: bold;
}


ul {
	list-style-type: square;
}

hr {
	height: 0px; 
	border: solid #D1D7DC 0px; 
	border-top-width: 1px;
}

```

To get the websites css I just went to View > Page Source then search the source(ctrl-f) for .css. Just click the link that shows up that ends with .css.

---

### Post by RealG187 on 2009-11-15
The two objects that I want to have different colors call on the same css.

---

### Post by tjwoosta on 2009-11-15
Unfortunately when writing userstyles you have no control over the html. You just have to try to work around it.

I would just do something like this (except with your own colors or whatever). Its not exactly ideal, but it works and doesn't look too bad.

```

@namespace url(http://www.w3.org/1999/xhtml);

@-moz-document domain("psphomebrew.net") {


* {
background: #262626 !important;
color: #9a9a9a !important;
border-color: #3e3e3e !important;
}

td .text {
background: #3e3e3e !important;
border: 1px solid !important;
border-color: #636363 !important;
}

td .smText {
background: #3e3e3e !important;
border: 1px solid !important;
border-color: #636363 !important;
}

td * {
border: none !important;
}

.text * {
background: none !important;
}

span.text {
background: none !important;
border: none !important;
}

span.bold {
background: none !important;
}

a.smLink {
background: none !important;
}

img[src*=".gif"] {
background: none !important;
}

}

```

Its basically a hack job, but hey. This sort of thing happens sometimes in userstyles because you don't have any control over the html itself. I basically just try to play around with things until it looks good and leave it.

---

### Post by tjwoosta on 2009-11-15
heres a pic showing the above style
[[img]http://omploader.org/tMnJ3YQ[/img]](http://omploader.org/vMnJ3YQ)


Also I forgot to mention when you asked about text, but you can change the color seperately for links, visited links, currently active links, and  hovering the mouse over links.


```

a:link {
color: whatevercolor !impoprtant;
}


a:active {
color: whatevercolor !important;
}

a:visited {
color: whatevercolor !important;
}

a:hover {
color: whatevercolor !important;
}


```

---

### Post by RealG187 on 2009-11-15
What did you do to change the color of the part that says
> Active Topics
Search
Help
Register
Login

---

### Post by tjwoosta on 2009-11-15
I think that part might have been colored with

```

* {
background: #262626 !important;
color: #9a9a9a !important;
border-color: #3e3e3e !important;
}

```

which basically colored everything dark grey, then I removed the border for that specific part with

```

td * {
border: none !important;
}

```


When you put a * after an object it makes the css work for any class/id within that main object. Like I said before I just played around with things until it looked alright.

I realize some of this is not exactly easy to understand, I still don't have a full understanding of much of it myself. I'm sure there are probably some great CSS courses online somewhere that could really help you out much better then I could. I'm basically self taught, and still learning as I go. The way I do things is ofter very hackish I know, but to tell you the truth most userstyles are.

---

