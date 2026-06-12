---
title: "Kompozer not responding"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by flyfishingphil on 2011-07-24
Have done everything I can think of but unable to open Kompozer. Icons show in both Internet and Programming, under file, but no response when clicked  on. Version downloaded and installed from Synaptic shows it to be 1:0.8-b3-2.

Any suggestions?

Built my site using Serif, in VBox using XP, but it doesn't view right with anything but windows. Checked with my Firefox browser and lots of problems there. Want to correct the site so it is viewable by all. Will Kompozer build a site that is workable by various browsers?

---

### Post by JC Cheloven on 2011-07-24
> **flyfishingphil said:**
>  Will Kompozer build a site that is workable by various browsers?
Web authoring experts usually say that every single WYSIWYG-like program for creating web pages is crap, and that html hand editing form scratch is the only way, despite the authors of such programs claiming that generated code will be W3C compliant
Well, as a non-expert person, I'd say that Kompozer worked fine for me to create and maintain some (three really) simple web pages I maintain since some years now. They're well seen both in win2 & linux, be it with ie, ff, epiphany, chrome...

Regarding your problem to run Kompozer: I'm running current LUbuntu and I have no problems with kompozer08b3, but I myself ran into a similar problem some releases ago (by the times of Hardy Heron). I solved it in this way: 

1) Download the compressed tar.gz file of kompozer for linux [from their site]("http://sourceforge.net/projects/kompozer/files/current/0.8b3/linux-i686/").
2) Extract to a place you find apropriate. If you have a ~/downloads folder that will do, but perhaps you may want to extract elsewhere, an external usb disk being also possible. A folder called "kompozer" will be created.
3) You're done!! To run kompozer simply go to that "kompozer" folder and run the shell script called "kompozer" by right-click on it or whatever.

Hope this helps :)

---

### Post by flyfishingphil on 2011-07-26
OK. Downloaded Kompozer 0.8b3.en-US.gcc4.2-i686.tar.gz

Clicked on it, searched thru the files, don't see an install option, cannot "open" it to try building a page or anything else.

What do I need to do to get it open and operational? SUDO install or something else? How to do needs to be in step-by-step.

Thanks for the help.

Just got to looking at the file info. Is the i686 version compatible with my laptop?

---

### Post by JC Cheloven on 2011-07-26
It's simpler than you think. Please follow the directives in my previous post CAREFULLY, they are correct and kompozer will work fine that way (well worked for me anytime I tried since Hardy). 

Further notes just in case:

- No "install" needed !!
- To uncompress the tar.gz you can simply right-click and choose "extract here".
- To run the kompozer shell script do as I said in my previous post.

Again, please read again my previous post, no void wording in it.

---

### Post by flyfishingphil on 2011-07-26
Doesn't offer the option to "Run".

Downloaded, saved to folder on desktop, did extract here, click on kompozer folder and offered options of:
open; open in new tab, open in new window; open with; cut; copy; paste; and the rest of the usual list.

open the folder and see lots of files but nothing that offers "run" option.

Have tried right click, left click, double left click. Program does not open from folder. Kompozer under Application> Internet or Programming does not open either. Same problem as before, just a different location.

Any other ideas?

---

### Post by bodhi.zazen on 2011-07-26
> **JC Cheloven said:**
> Web authoring experts usually say that every single WYSIWYG-like program for creating web pages is crap, and that html hand editing form scratch is the only way, despite the authors of such programs claiming that generated code will be W3C compliant
Well, as a non-expert person, I'd say that Kompozer worked fine for me to create and maintain some (three really) simple web pages I maintain since some years now. They're well seen both in win2 & linux, be it with ie, ff, epiphany, chrome...

There is nothing wrong with using WYSIWYG programs when first starting, or a small number of "simple" pages, however ... 

There is a reason why "the experts" recommended you not use these programs, lol

The code they generate is sloppy and in the long run, IMO, it is better to learn to use other tools.

Once you learn the underlying code, try to migrate to tools such as bluefish , gedit, or honestly I use vim.

Of the three, bluefish may be the best if you are migrating from a WYSIWYG editor.

But do not dismiss gedit so fast :

[http://www.micahcarrick.com/gedit-html-editor.html](http://www.micahcarrick.com/gedit-html-editor.html)

You then view your pages with a browser, such as firefox and midoiri. Nothing like viewing the page in a few browsers ;)

Just because your page passes a html validator does not mean it renders properly in all browsers (unfortunately browsers are often quirky to say the least when rendering html pages).

Learning the syntax of html and css pays off in spades.

At any rate, @flyfishingphil - The first step is to try to run your page through a html validating service :

[http://validator.w3.org/](http://validator.w3.org/)

The second step, and here is where WYSIWYG editors are a pain, view the code with gedit or bluefish and find and fix the errors the editor injected.

I will warn you, it is often easier to copy - paste your text then it is to find the error.

If you attach your html file as a text file I we can take a peek to see what , if any, problems it has.

---

### Post by flyfishingphil on 2011-07-26
bodhi...

Thanks for the response. Wouldn't mind doing Bluefish but have tried it and don't seem to be able to get it started. Don't have an HTML manual handy, to get directions from, had a head injury so have a hard time retaining directions I've read, so WYSIWYG has worked best for me. Did a validation check and, apparently, the Serif program I purchased made about 500 errors in the process.

Looks like what I may need to do is break out a "for dummies" book I have and see if I can build from scratch. Scary thought! Have a bunch of pages with photos, etc, and not sure how to do the text insert for review. Besides there are too many pages to do that with anyway. 

I'll look into your suggestions and see what I can come up with to make HTML work right. Kompozer sure doesn't want to work for me. Is there a listing of HTML commands anywhere, like inserting a photo, an order tab, and email link?

Thanks again for the assist offer.

---

### Post by alphacrucis2 on 2011-07-27
As an aside there is a new wysiwyg editor available called [bluegriffon]("http://bluegriffon.org/"). The dev is the original developer of NVU from which Kompozer was forked. (it isn't in the ubuntu repos currently).  One thing is that there are several useful addons but they are not free unfortunately.

I disagree with the comments about the value of wysiwyg tools. A text editor may be great for development but is horrible for content maintenance. Kompozer would be great if it combined a good text editor with the wysiwyg. Unfortunately the text source editor in Kompozer kind of sucks.

---

### Post by flyfishingphil on 2011-07-27
What are the steps to downloading and installing the installer and program for BlueGriffon? It says to do permissions and settings but that leaves me in the dust. 

Step-by-step instructions needed by a brain damaged user!

---

### Post by alphacrucis2 on 2011-07-27
> **flyfishingphil said:**
> What are the steps to downloading and installing the installer and program for BlueGriffon? It says to do permissions and settings but that leaves me in the dust. 

Step-by-step instructions needed by a brain damaged user!


Just right click on the downloaded installer in nautilus and select properties - permissions. Then tick allow executing file. Then from a terminal window:

cd <whereever I downloaded it> eg cd Downloads
./BlueGriffon-1.1.1-Linux-x86_64-Install

Note - that assumes you downloaded the 64 bit version. Change the above to the actual name of the installer you downloaded. Note that Linux file names are case sensitive.

---

### Post by mastablasta on 2011-07-27
try downloading the Ubuntu 10.10 installer. [http://bluegriffon.org/pages/Download](http://bluegriffon.org/pages/Download)
 
instructions are on the site.
 
if you download the .tar file extract it and read insctructions within that file.
 
w3.org site has HTML commands as well as online school/training for HTML.
 
kompozer is realyl unfinished business. however bluefish should work just fine. haven't tried the bluegriffon yet, but looks interesting

---

### Post by flyfishingphil on 2011-07-27
OK, downloaded and saved to Desktop. Here's what I get using Terminal and doing the entry that you sent. What am I doing wrong now? (ARRRGGGHHHH!!!!)

cd Desktop./BlueGriffon-1.1.1-Linux-x86_32-Install
bash: cd: Desktop./BlueGriffon-1.1.1-Linux-x86_32-Install: No such file or directory

Did the permissions, the BlueGriffon icon is on the desktop and no luck. Going to bed now. Will try again after getting some sleep.

---

### Post by alphacrucis2 on 2011-07-27
> **flyfishingphil said:**
> OK, downloaded and saved to Desktop. Here's what I get using Terminal and doing the entry that you sent. What am I doing wrong now? (ARRRGGGHHHH!!!!)

cd Desktop./BlueGriffon-1.1.1-Linux-x86_32-Install
bash: cd: Desktop./BlueGriffon-1.1.1-Linux-x86_32-Install: No such file or directory

Did the permissions, the BlueGriffon icon is on the desktop and no luck. Going to bed now. Will try again after getting some sleep.

It's two different commands which you have run together. First:

```
cd Desktop
```

Hit the Enter key. 

That changes the current directory. Then the ./ prefix is used to run the installer:

```
./BlueGriffon-1.1.1-Linux-x86_32-Install
```

Hit the Enter key.

---

### Post by bodhi.zazen on 2011-07-27
If / when you are interested, there are many on line tutorials

[http://w3schools.com/html/](http://w3schools.com/html/)

Bluefish and the link I gave you on gedit both have the html tags built into the menu, ie they are graphical.

Screenshots are here:

[http://bluefish.openoffice.nl/screenshots.html](http://bluefish.openoffice.nl/screenshots.html)

The guide is here:

[http://bluefish.openoffice.nl/manual/bk01-toc.html](http://bluefish.openoffice.nl/manual/bk01-toc.html) 

It is detailed (yes, you can skip the installation section for example) and includes screenshots.

What is wrong with WYSIWYG editors ???

1. > Did a validation check and, apparently, the Serif program I purchased made about 500 errors in the process.

Those errors will eventually cause a problem, and you will need to then dive into the code and fix them.

Unless you know the underlying HTML, it will be difficult or impossible to fix, and it is much easier to learn to write good code then fix bad code ;)

2. The only true WYSIWYG is to open the file with a browser, preferably at least 3 - Firefox, Chromium, and IE.

So yes, they are fine as an initial learning tool, but for large and complex pages, you will have more problems in the long run.

I am just trying to save you a bit of time, I have been there done that.

good luck to you with BlueGriffon ;)

---

### Post by flyfishingphil on 2011-07-27
Thanks all for the assists. Found out, by accident, how to get the BlueGriffon installed and operational. Accidentally double left clicked on it this morning while trying to take a look at what it might have in it. That did the extract and install and it is now operational. (Funny how even the mentally feeble can make something work by accident!)

Now all I need to do is find the "how-to" for the BlueGriffon and I can see how bad I can foul that up!

Also, FYI, I was looking at saving something in OpenOffice and noticed that it offers both save in HTML and setting up a web page. Will take a look at that and see what it offers, and if it is easily posted using ftp. Will put info here as soon as I have figured it out.

Thanks again for the assists and, if you know of a good resource for working HTML's, like BlueGriffon, please let me know.

---

### Post by bodhi.zazen on 2011-07-27
I took BlueGriffin for a spin, and honestly it is no easier then Bluefish, IMHO.

The document does not look the same in the WYSIWYG editor as it does in firefox .

The resulting document was valid, but quite complex.

It did not include my background image as requested.

In terms of the code, IMO, it inserted some unnecessary html, in particular <br>

I have attached the two files. The simple file does not have any css mind you, but the css would be simple to write.

In general you are going to want to break up your documents as it makes your pages easier to read and your web site easier to maintain.

html - content
css - style / layout
js - behavior

If you have multiple pages, you call the css or js from external files. If you want to change your layout / background you would make an edit to your css and it would effect your entire site.

If you use the complex pages generated by BG your are going to make extra work for yourself later , when you want to change. Even a simple edit, such as changing a color, will mean finding and editing multiple complex html files.

Also look at the size of the files, the BG file is 8.4 Kb !! That is huge for what it is. This will affect your bandwidth and server performance.

Save the attached files, change the name from.txt to .html (BG.html and simple.html) and open them with firefox ;)

Ask yourself, which page is going to be easier to maintain, the simple text or the BG text.

---

### Post by flyfishingphil on 2011-07-27
TNX bodhi! Opened those up in Firefox and looked at page source. Simple looks like it would work much better for me! BG has about 100 lines more than the simple.txt (html) so a couple of questions:

Where do I find that simple text format to work in? Is that gedit?
Will the majority of the browsers read the simplehtml the same?

Guess I'll go to the w3 school listed above and print out the HTML guide and see what I can do.

---

### Post by bodhi.zazen on 2011-07-27
> **flyfishingphil said:**
> TNX bodhi! Opened those up in Firefox and looked at page source. Simple looks like it would work much better for me! BG has about 100 lines more than the simple.txt (html) so a couple of questions:

Where do I find that simple text format to work in? Is that gedit?
Will the majority of the browsers read the simplehtml the same?

Guess I'll go to the w3 school listed above and print out the HTML guide and see what I can do.

I hand wrote simple in gedit. Once you learn the html it is easy, there are only a handful of tags.

There are a few tricks, including learning to use divisions, class, and id, but it will come.

simple.html should look about the same in all browsers.

Personally I advise you migrate from a WYSIWYG technique to bluefish or gedit.

Bluefish has a number of tools including syntax highlighting and auto completion.

So if you start a html tag, <h1> , bluefish closes the tag

<h1></h1>

with your cursor in between. 

All the html tags are available from the menus (so no you do not need to memorize them) Bluefish is as easy to use as a WYSIWYG editor ;)

[img]http://www.davepcguy.com/wp-content/uploads/2010/06/screenshot13.png[/img]

The only major difference with bluefish, you will see the code directly, you then view the file with firefox .

Take a look at this layout

[http://zenix-os.net/screenshots.html](http://zenix-os.net/screenshots.html)

View page source, very simple and straight forward

(In firefox View -> page source).

To position the elements you use css.

[http://zenix-os.net/style.css](http://zenix-os.net/style.css)

If I change an image, edit the first file

The second file, the css, applies to all pages on that site. So if I change the background image, one edit in that style.css and all pages are changed.

Your css tutorial is here :

[http://www.w3schools.com/css/css_howto.asp](http://www.w3schools.com/css/css_howto.asp)

Yes, bluefish does css too ;)

Again, use the links I gave you as reference, and you will find the code / tags in bluefish, all at the click of a button.

Edit: Do not let that css page intimidate you, as I indicated, it applies to all pages on the site, so that style.css is also used for [http://zenix-os.net/features.html](http://zenix-os.net/features.html) , that is the beauty / simplicity of a separate css .

Yes it feels more complex at first, but trust me, learning to write clean code pays off in spades. Much easier to maintain, much easier to edit, and much easier to debug.

---

### Post by flyfishingphil on 2011-07-27
Sure is nice finding people willing to spend the time leading a blind guy down a rugged mountain trail!

I'll add the w3 site to my bar and spend a lot of time there with the html instructions. The good part is it's not a matter of life or death that I get the site replaced immediately so I can take the time to learn in trial and error.

Initially the start page at Bluefish looks like a foreign language, maybe Vulcan, but you're probably right about once you get it working it more than makes up for the ease of WYSIWYG.

BTW, do I need to save what I am working on to a folder before I can view the progress in Firefox? Any ease of doing tricks there?

---

### Post by bodhi.zazen on 2011-07-27
> **flyfishingphil said:**
> BTW, do I need to save what I am working on to a folder before I can view the progress in Firefox? Any ease of doing tricks there?

Open the file with Bluefish and Firefox. Make any edits you like and save your changes, then refresh the page in Firefox to see the changes.

If you are a keyboard person, ctrl-R

---

### Post by flyfishingphil on 2011-07-27
Just did a copy and paste from site to Bluefish. Experimented for a few adding in the html commands (<body/> <p>) and it looks like using the w3html manual and experimenting that way may actually make it workable.

I'll play with it some more and let you know how it goes.

Thanks again for all of the help. Looks like I'm getting paid back for helping some others fix some problems I was aware of how to fix.

---

### Post by JC Cheloven on 2011-07-27
[COLOR="Red"]**@ flyfishingphil: PLEASEEE LOOK INSIDE THE FOLDER CALLED KOMPOZER, THERE IS A FILE ALSO CALLED KOMPOZER (WHICH IS A BASH SCRIPT). BUT A FILE IS DIFFERENT FROM A FOLDER, RIGHT??**[/COLOR]
So, please, get into the folder called kompozer. There, inside, is a FILE callled kompozer, without any extension. It is a bash script, which is what you have to run. Right-click to it. [COLOR="DarkRed"]**Choose open**[/COLOR]. You'll be presented with a dialog box with some options (see attached screenshot). The dialog says something like [COLOR="DarkRed"]**"This text file seems to be a executable script, what do you want to do?"**[/COLOR]. Then the buttons with the options to: 1) execute. 2) Execute at a terminal. 3) Open. 4) Cancel.

Please [COLOR="DarkRed"]**choose the first one**[/COLOR] "Execute". Kompozer will open nicely for you.

Sigh :cry:

---

### Post by flyfishingphil on 2011-07-27
Thanks for the clarification of what I am looking for now, if that file was in the one that I have, it might work better. I'll dump the one I have and do a fresh download and see if it comes thru. If it does I'll try it and see but, for right now, I'm also looking into the HTML method of building my site. Looks a bit challenging, from what I have learned in the last few days, however it may be the best way to go.

I'll edit this response, after a retry at download, if ti comes thru as described and works properly.

OK, got a fresh one. This is different from the one you are using in what is offered. The choice are:

Run in terminal

Display

Cancel

Run

Click the "Run in terminal" and it opens the program. 

I clicked on that file before but nothing happened with the one I had downloaded before. This one jumps right in so I'll give it a look while I play with the html/css info provided above at W3.

---

### Post by bodhi.zazen on 2011-07-27
Just fired up bulefish (dueling methodologies)


To generate a new document 

File -> New from template -> html5

This gives you a basic html 5 document.

Add an external css

Dialogs -> Css -> Link to style sheet

Fill in the pop up menu, call the style sheet "sytle.css" with a href of ./style.css

Open a new document and save it as style.css.

Now start typing , use the html tag for html, and the css tag for css

If you start typing b for border, you will get a pop up menu of the tags ;)

To view the document, 

Tools -> Firefox opens the html document in firefox.

After making an edit, save you changes and refresh firefox.

---

### Post by flyfishingphil on 2011-07-28
Thanks bodhi. Printed your page so I can start building a library to refer to while learning the process. Also keeping a list of what I can't figure out yet so I can refer that over for assist if, when needed.

OK, tried what is on your tip above. Went to File but found nothing listing template. Am I misreading or is there something else I need to do to get the templates?

---

### Post by bodhi.zazen on 2011-07-28
What version of bluefish ?

Should be second on the list under "File"

New From Template

---

### Post by kaldor on 2011-07-28
Great advice from Bodhi. Learning HTML yourself will save you a LOT of headaches in the future. WYSIWYG will only make sites more and more unworkable as you keep at it.

You've got the right method right now; learn HTML as you use a WYSIWYG to lean back on. Eventually you won't even need it :)

---

### Post by lisati on 2011-07-28
> **bodhi.zazen said:**
> I took BlueGriffin for a spin, and honestly it is no easier then Bluefish, IMHO.

The document does not look the same in the WYSIWYG editor as it does in firefox .

The resulting document was valid, but quite complex.

It did not include my background image as requested.

In terms of the code, IMO, it inserted some unnecessary html, in particular <br>

I have attached the two files. The simple file does not have any css mind you, but the css would be simple to write.

In general you are going to want to break up your documents as it makes your pages easier to read and your web site easier to maintain.

html - content
css - style / layout
js - behavior

If you have multiple pages, you call the css or js from external files. If you want to change your layout / background you would make an edit to your css and it would effect your entire site.

If you use the complex pages generated by BG your are going to make extra work for yourself later , when you want to change. Even a simple edit, such as changing a color, will mean finding and editing multiple complex html files.

Also look at the size of the files, the BG file is 8.4 Kb !! That is huge for what it is. This will affect your bandwidth and server performance.

Save the attached files, change the name from.txt to .html (BG.html and simple.html) and open them with firefox ;)

Ask yourself, which page is going to be easier to maintain, the simple text or the BG text.

Eeek! Bloat! At least it's formatted a bit more nicely than some I've seen made using Serif.

---

### Post by bodhi.zazen on 2011-07-28
> **kaldor said:**
> Great advice from Bodhi. Learning HTML yourself will save you a LOT of headaches in the future. WYSIWYG will only make sites more and more unworkable as you keep at it.

You've got the right method right now; learn HTML as you use a WYSIWYG to lean back on. Eventually you won't even need it :)

Thanks for your support in this thread.

I agree, there is nothing wrong with WYSIWYG editors so long as you use them as a learning tool.

In the long run learn the html and css (and js / php). 

If you do not , and continue to use the WYSIWYG editors your web pages become more and more cumbersome to manage.

Just understand, the WYSIWYG editors add a fair amount of "bloat" , and that bloat makes appear harder then it actually is (see the two files I posted earlier, and the links to my website, the BG file is much longer (for what it renders in a browser) and more difficult to understand).

---

### Post by flyfishingphil on 2011-07-28
> **bodhi.zazen said:**
> What version of bluefish ?

Should be second on the list under "File"

New From Template

It's version 1.0.7. The File options are    New,  New window,    Open,   Open Recent,    Open Advanced,     Open URL,    Open From Selection, etc. That's the version available in Ubuntu Software Center and Synaptic.

Looked for "bluefish editor download" and went to [http://bluefish.openoffice.nl/download.html](http://bluefish.openoffice.nl/download.html) and looked at 2.0.3 but don't see the usual "download" method. How do I get the newer version, if that's what I need?

Found and downloaded bluefish-2.0.3.tar.gz and extracted so have the folder but that's as far as I can get. How do I install from this point, or do I need to do some other steps before I can install the newer version? The instructions seem to be written for someone that already knows the "how-to" and aren't aimed at the "first-timer". (Clicked on install, that gives directions that I'm not used to. Clicked Install-sh then tried both Run in Terminal and Run but got nothing.)

---

### Post by bodhi.zazen on 2011-07-28
Ah

There is a repository (and instructions) for bluefish here :

[http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.0_on_Ubuntu](http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.0_on_Ubuntu)

---

### Post by flyfishingphil on 2011-07-28
Looked at that. Did the sudo and it installed the 1.0.7 from the Linux software not the newer version. So, what do I need to do to get the newer version in and installed?

OK, I catch on when given enough time. Downloaded the Bluefish 2.0.3 and it wouldn't install. Downloaded the Data, installed. Downloaded Add-ons, installed. Went back to Bluefish 2.0.3 and it finally installed! Interesting how there doesn't seem to be any directions saying the others need to be installed before you can install the main program.

Will play around with the new version and see what else I can do wrong.

---

### Post by bodhi.zazen on 2011-07-28
OK, as long as it is working there is no need to change.

Normally one adds a repository

There are instructions on doing that here:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Other%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Other%20Repositories)

Although you can add repositories in several ways ;)

---

### Post by flyfishingphil on 2011-07-28
Shows how up to speed I am. I thought the Repositories were done at/by Ubuntu, not the users. Still exploring to find out what it will do. 

Looks like I need to "update" my terminology. Still haven't figured out how/where to build the "index.html" page, like I did in Serif, to use as the base page to build all of the others on. May order and "HTML fo Dummies" book before I go much further.

---

### Post by bodhi.zazen on 2011-07-28
> **flyfishingphil said:**
> Shows how up to speed I am. I thought the Repositories were done at/by Ubuntu, not the users. Still exploring to find out what it will do. 

Looks like I need to "update" my terminology. Still haven't figured out how/where to build the "index.html" page, like I did in Serif, to use as the base page to build all of the others on. May order and "HTML fo Dummies" book before I go much further.

Personally I save my files in ~/Documents/web

As they start to get complex / large number of pages I start to make sub directories

~/Documents/web/css
~/Documents/web/php

and on ;)

Choose a directory structure that works for you.

When I think of an index.html I think of a few elements

What is the theme going to be ? 
What is the navigation (menu) going to be ?

IMO, with large sites, it is easier to source a menu, for that I use php.

So then I have one menu, say menu.html, that is pulled into all my pages by php. 

That way, if I have to update my navigation, it is only updating one menu.html and not each and every page.

So you index.html is a template

html
header
navigation (menus)
body
footer

leave the body blank, that will vary with each page.

```
<!DOCTYPE html>
<html>
<head>
<meta http-equiv="content-type" content="text/html; charset=UTF-8">
<link rel="stylesheet" type="text/css" href="./style.css" />
<title>index page</title>
</head>
<nav>your menu goes here, php or otherwise</nav>
<body>
<h1>Header / title</h1>
<p>This is a template, your content goes here.</p>
</body>
</html>
```


Are you starting to see a theme here ?

Again, you can not learn all this at once. 

There are many methods to structure you page, google search html5 layouts

[http://www.my-html-codes.com/html-5-coding](http://www.my-html-codes.com/html-5-coding)

Books are not as helpful, imo, work through the links I gave you first.

---

### Post by flyfishingphil on 2011-07-28
Thanks again. Just got back from a run to Barnes & Noble to get a book on HTML and had good fortune there. 

Seems the guy working there has done HTMl, and web site building, in the past and recommended a book other than "Dummies". His thought, on making it easy, is to set up the first page exactly as you want it then you can copy/paste that same info onto each page as you develop it. This carries all of the same info to each page then, if you want to later, you can easily change just one page and not the entire site.  Wound up with a book by Elizabeth Castro, called HTML, XHTML & CSS, that's a "visual quickstart guide" (Updated 6th Edition). 

It's full of step-by-step instructions, with all of the "stuff" needed to build pages and it has color photos of the results, lots of "how-to's" on doing things like italics, etc.

Spend a couple of days going thru the book to get some basic understanding then I'll go to work (probably use gedit for practice) on doing the samples in the book so I can better grasp what I'm doing. Hopefully it won't take more than a couple of years to get it done! (LOL)

I'll check out the HTML5 ref and bookmark that too.

---

### Post by flyfishingphil on 2011-08-01
bodhi,

OK, followed your suggestions, picked up a book on html (a Teach yourself visually: Web Design) and have been playing around in gedit. A little time consuming, but I see the value by jumping from building to viewing: find any errors and correct them immediately.

Im trying to build a template to use for each page that shows the logo, title and photo at the top of the page and a footer. (Footer not done yet) 

One thing I haven't been able to find an answer for is centering the boxes at the top of the page that have the logo in the left side, site title in the center, and a photo of self in right side. 

Also, what do I need to do to set it up to "auto resize" to fit the viewing screen?

Tried to load the file but it said it's and invalid file so I copied and pasted it so you could take a look at it.

Thanks. flyfishingphil

ffp Compound Rods proposed template (under development)

<!DOCTYPE HTML PUBLIC "-//W3c//DTD HTML 4.01 Transitional//EN ">
<html><head>
<meta http-equiv="content-type" content="text/html; charset=ISO-8859-1">


  
 <title>index.html</title></head><body style="height: 235px;">


<table style="text-align: left; width: 1000px; height: 213px;" border="1" cellpadding="2" cellspacing="2">

  <tbody>

    <tr><td style="vertical-align; top; horizontal-align; center; width: 220px;"><img style="width: 222px; height: 255px;" alt="ffpC-Rods logo" src="index_files/ffpRodslogo.jpg"><br>
      </td>
      <td style="vertical-align: top; width: 760px; text-align: center;"><br>
      <h2>Welcome to ffpC-Rods</h2>
      <h4>The home of the incomparable Compound Fishing Rods<br>
      </h4>
      <br><h5> Email: <a href="mailto:flyfishingphil@ffpc-rods.com">flyfishingphil@ffpc-rods.com</a><br></h5><h5>Cell 541-778-0963</h5>
      </td>
     
      
      <td style="vertical-align: top; width: 223px;"><img style="width: 220px; height: 187px;" alt="flyfishingphil photo" src="index_files/Intro%2520insert.jpg"><br>
      </td>
    </tr>
  </tbody>
</table>

<br>

<br>
<div style="margin-left: 40px; text-align: center;">On Site Pages:<br><br>
<a href= "index.html"> Home</a href>&nbsp;&nbsp; <a href= "page-3"> Choosing the best rod for you</a href>&nbsp;&nbsp;<a href= "page-4"> Compound Fly
Rods</a href>&nbsp;&nbsp; <a href= "page-5"> Compound Spin Rods</a href>&nbsp;&nbsp; <a href=page-6> Compound Bait
Rods</a href>&nbsp;&nbsp; <p><a href= "page-7"> Discounted Fly Rods</a href>&nbsp;&nbsp; <a href= "page-8">Special Ordering a Compound Rod</a href>&nbsp;&nbsp; <a href= "page-9">C-Rod Repairs</a href>&nbsp;&nbsp; <a href= "page-10"> Who invented the
C-Rod?</a href>&nbsp;&nbsp; </p><p> <a href= "page-11"> Who is this ffp?</a href>&nbsp;&nbsp; <a href= "page-12"> Building the C-Rod</a href>&nbsp;&nbsp; <a href= "page-13">The "Techie" page</a href>&nbsp;&nbsp; <a href= "page-14"> C-Rod FAQ's</a href>&nbsp;&nbsp; <a href= "page15">What does the C mean?</a h ref>&nbsp;&nbsp; </p><p>
<a href= "page-16">"That won't work!"</ a href>&nbsp;&nbsp;  <a href= "page-17">The Fly Casting Exercise</a href>&nbsp;&nbsp;  <a href= "page-18">Where to fish cd's</a href>&nbsp;&nbsp;  <a href= "page-19">Trusted Links</a href><br>

---

### Post by bodhi.zazen on 2011-08-01
Hey, that page is looking nice =)

Depends on what you want, try

```
<table style="text-align: left; width: 1000px; height: 213px; [color=blue]margin: 0px auto;[/color]" border="1" cellpadding="2" cellspacing="2">
```

or if you wish some space at the top

```
<table style="text-align: left; width: 1000px; height: 213px; [color=blue]margin: 10px auto;[/color]" border="1" cellpadding="2" cellspacing="2">
```

You can put your css in a separate file

```
<table id="header" style="text-align: left; width: 1000px; height: 213px; margin: 0px auto" border="1" cellpadding="2" cellspacing="2">
```

Notice how I pulled the "style" ? ^^

Now in your css file put

```
#header {
text-align: left;
width: 1000px;
height: 213px;
margin: 0px auto
}
```

And on with all your styles ;)

You then use the same css file for all your pages.

Also, close your links with a </a> and not </a href>

Attached is some work I did on your page ;)

---

### Post by flyfishingphil on 2011-08-01
Merci Beaucoup! Domo Arrigato! Muchas Gracias!

Did the changes to mine and it looks fine. Now all I have to do is add the footer then I can save it as each of the pages and fill in the "blanks" for each page.

BTW, in the WYSIWYG format I used before it had a "structure" (?) for the pages to keep them in order. Stared with the "HOME" page then placed the others as "subs" to that page. Do I need to do that using Bluefish? Don't know what I'm looking for so don't know where to look for it.

---

### Post by bodhi.zazen on 2011-08-01
Do not expect perfection with your first web pages.

Over time you will learn to revise them.

Look at other web sites and play with css . Use your book or google for effects.

I would consider your links to be "menus" or "navigation"

See: [http://www.seoconsultants.com/css/menus/tutorial/](http://www.seoconsultants.com/css/menus/tutorial/)

Next we shall teach you php, with php you can write just such a menu in a separate and include it on all your web pages.

The "trick" of maintaining a web site is to break it into chunks you can use on all your pages.

html = content
css = layout - use a single external css file for all your pages.
js = behavior
php = scripting / automating. Write a single file with your navigation and use php to include it on all your pages (rather then writing a menu on each page).

One step at a time, start with content and layout. Once you have a well designed home page, you can pull the style into an external css and menu into a php or javascript.

Many methods exist to make your content easy to manage. Just keep learning.

---

### Post by flyfishingphil on 2011-08-01
That's what I'm doing with the page we bounced. Use that as the "base" page and add the contents for all of the different subjects as separate pages. Gives some continuity to the site, saves a lot of time, once it is fully prepared, and makes it much easier to go in and make changes as needed on individual pages.

I'll check out your web ref and see what it has to say. "The more I read the less I know!"

---

### Post by flyfishingphil on 2011-08-07
bodhi-next question re: "posting the website via ftp"

I think the building part is done.(All 19 pages with photos, forms, etc.) Everything seems to be in the right place, when browsing with Firefox, and looks good. Just can't "test" the PayPal connection because it's not on the "net" to connect. Now, the next "How-to".

How/what do I use to do the ftp to get the site to dot5 and replace my old version?

The Serif I used before had it built in but I don't "see" it in Bluefish.

From what I see in my "Teach yourself visually" web design book I need to put the "index.html" in the "root" folder and build additional folders but can't figure that part out either. Anybody know where to find the steps, or do I need to get those directly from dot5 for their site?

Thanks again.

Have tried FireFTP but don't seem to be doing something right. Instructions on steps at dot5 hosting are for filezilla, have FileZilla 3.5.0_i586-linux-gnu.tar.bz2 on my desktop but don't remember how to install. Any help there?

---

### Post by bodhi.zazen on 2011-08-08
Well, ftp is just one of several methods of transferring the files.

Personally I use scp, more secure, but most web designers still use ftp.

At any rate , it depends on how your hosting works.

Make a copy of your current files, and transfer the new set in.

The default location is /var/www , but , with shared hosting it could be most any location.

Contact your provider and ask for assistance. Some providers have nice web interfaces =)

If you do not understand what they tell you, post the information here.

---

### Post by flyfishingphil on 2011-08-08
Thanks for response. Getting a little disappointed in the dot5 tech support. 

 Just had one say if I'm having problems getting my site working right I should go to a link he provided and, guess what! Go to the link and it's a page with all of the options for getting your site working right by "hiring" technicians and paying a monthly fee. 

Kinda makes me wonder. They used to be real helpful.

I can get the Home page up and open, but none of the others. About to go crazy trying to figure this one out. Book says do this, they say don't do that. Guess I'll keep trying.

EDIT:
Got it working. Book said to add in a forward slash at the end of the <a href="page-2.html/. Tech there said to remove the forward slash. Seemed to be what was needed. Now all I have to do is figure out how to put the photos into the files so the site pages have them.

---

### Post by flyfishingphil on 2011-08-08
Thanks for the help all. Decided to follow bodhi's recommendations and built the site using a book and gEdit, uploaded using FireFTP, with help of tech's at dot5 got it all working.

Guess I'll stay with the book and gEdit. Once you get the hang of it, not bad.

Call this case "Solved"!

---

