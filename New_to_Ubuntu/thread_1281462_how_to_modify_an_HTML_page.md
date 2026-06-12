---
title: "how to modify an HTML page"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by jrev on 2009-10-03
hi all,

I wish I can suppress some "line feed" in an HTML page in order to reduce it a bit so that it prints on one page on my printer (and not one page and 2 lines on the second page)
This is a recurring problem which deserves a wiki page (or two)

ubuntu proposed me "screem" but I do not know where to start.

Can you show me the way ?

Thanks

---

### Post by cogier on 2009-10-03
I have created and edited HTML files in Open Office Writer which is probably installed already. Right click on the HTML file and Open With OpenOffice.org Word Processor

---

### Post by erilidon on 2009-10-03
I know with my printer you can simply go into the properties and change the "scaling" option.

---

### Post by NoaHall on 2009-10-03
You can use gedit, or anything.
ctrl + u to see source code, copy and paste into gedit, print.

---

### Post by jrev on 2009-10-03
> **NoaHall said:**
> You can use gedit, or anything.
ctrl + u to see source code, copy and paste into gedit, print.

Yes Noa, but with gedit I only see the code and not the lines.

If I knew the code for "line feed" or "carriage return" i could probably suppress some, especially when there is a number of them together !

In fact they are xls pages converted into HTML and I wish I can put them back into the original format in order to suppress some lines.
Or be able to see the page in "screem" and be able to suppress the lines as I do in word or in openOffice writer.

I did it before with an old html editor whose name I cannot remember...

---

### Post by the.phantom on 2009-10-03
might just "comment out" the things you do not what to see?


The starting comment tag is <!-- (that's the 'lesser than' sign followed by an exclamation mark and two dashes) and the ending tag is -->
then you could easly edit them out when finished

---

### Post by scragar on 2009-10-03
Install the firebug plugin, edit the pages source using it, print.

---

### Post by jrev on 2009-10-03
the only thing I still have to learn : 

What is the code for "line feed" and "carriage return"

in order to be able to suppress some of them...

**Thanks for all those good answers**

---

### Post by Kapitän Rotbart on 2009-10-03
Use Adblock Plus's blocking image feature on right-click? Easy way to trim out a few things in a web page (and that's not limited to HTML).

---

### Post by jrev on 2009-10-03
> **Kapitän Rotbart said:**
> Use Adblock Plus's blocking image feature on right-click? Easy way to trim out a few things in a web page (and that's not limited to HTML).

Right click on the html page ? 
Could you give me more details ?

---

### Post by Jim_in_Germany on 2009-10-03
Hi,
Could you give me a bit more information on what exactly you want to do?
Do you want to print a web page as it appears in Firefox?
If so, press ctrl+p, select page setup and you can scale the page accordingly (100% - 1%)
Or do you want to manually edit the html code of a web page (that you have saved locally on your computer) so that it will then fit onto one page?
If this is what you are trying to do then the code for a line break is <br />
You can open any html document with a simple editor like gedit, or you can install kompozer (sudo apt-get install kompozer), which is a wysiwyg editor. 
Using that you can make any changes you want to the page.
Or are you trying to do something different altogether?

---

### Post by scragar on 2009-10-03
> **Jim_in_Germany said:**
> Hi,
Could you give me a bit more information on what exactly you want to do?
Do you want to print a web page as it appears in Firefox?
If so, press ctrl+p, select page setup and you can scale the page accordingly (100% - 1%)
Or do you want to manually edit the html code of a web page (that you have saved locally on your computer) so that it will then fit onto one page?
If this is what you are trying to do then the code for a line break is 
<br />
Or are you trying to do something different altogether?

You've also got paragraphs:
```
<p>Content</p>
<p>Another paragraph.</p>
```

---

### Post by Jim_in_Germany on 2009-10-03
> You've also got paragraphs:
Code:
[HTML]<p>Content</p>
<p>Another paragraph.</p>[/HTML]

Indeed, or many other tags that will cause a browser to render a new line, such as <h1>.

---

### Post by gordintoronto on 2009-10-03
<br> is the most likely code for a new line.

To do what you want, why don't you select File/Save Page as/Text File, then pull the result into Gedit where you can play with it as you wish.  Probably, you could even import the result of that into Open Office spreadsheet, using space as a field delimiter.

---

### Post by jrev on 2009-10-04
Here is the code of the web page to modify in order to print it :

In fact I cannot show you the code for the following reason :

<You have included 68 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.>

But you can go to :

[http://forum.ubuntu-fr.org/viewtopic.php?id=347354](http://forum.ubuntu-fr.org/viewtopic.php?id=347354) 
to see the code on post #7

Thanks you for your patience to sort out my problem !

---

### Post by ad_267 on 2009-10-04
> **gordintoronto said:**
> <br> is the most likely code for a new line.

I hardly ever use the <br /> tag when creating a website. Paragraphs should be defined using <p> tags, and the cases where you want to start a new line within a paragraph are pretty few and far between.

Jrev, it looks like the html you posted in that thread isn't complete, so it's hard to help. Changing the html using Firebug or the Web developer add-on is probably the easiest way to do what you want.

Edit: You could just attach the html file to your post.

---

### Post by Paqman on 2009-10-04
The layout of that page seems to be defined in the header, within the <style> tags. If you edit out all of that, it'll give you plain text.

---

### Post by jrev on 2009-10-04
The solution was :

Delete all blocks starting with <tr>  and ending with </tr> where there is no information. 
Every such block accounts for a new line in the table to print.

Thanks for your help :P

---

### Post by scragar on 2009-10-04
> **jrev said:**
> The solution was :

Delete all blocks starting with <tr>  and ending with </tr> where there is no information. 
Every such block accounts for a new line in the table to print.

Thanks for your help :P

Tables? Whoever the developer is should be ashamed of themselves.

---

### Post by ikisham on 2009-10-04
[This]("https://addons.mozilla.org/en-US/firefox/addon/951") addon allows you to remove undesired elements before printing.

---

### Post by Paqman on 2009-10-04
> **scragar said:**
> Tables? Whoever the developer is should be ashamed of themselves.

You'd be amazed how many people still think it's a good way to build a site.

---

### Post by scragar on 2009-10-04
> **Paqman said:**
> You'd be amazed how many people still think it's a good way to build a site.

Well it is for the first build, making something with tables is faster than making it with CSS, the problem comes that tables based sites are near-impossible to update and upgrade without a complete rebuild.

---

### Post by twright on 2009-10-04
> **scragar said:**
> Well it is for the first build, making something with tables is faster than making it with CSS, the problem comes that tables based sites are near-impossible to update and upgrade without a complete rebuild.
Tables easy? Only if you are using a WYSIWYG editor and that is a bad idea on a whole other level.

---

### Post by scragar on 2009-10-04
> **twright said:**
> Tables easy? Only if you are using a WYSIWYG editor and that is a bad idea on a whole other level.

Even in a text editor, if you've got what you're doing mapped out you can make tables layouts much easier than CSS, updating those layouts not so much(because your content winds up everywhere, there's no structure to the code, and every change changes the whole layout, not just the parts you want).

---

### Post by itsbrad212 on 2009-10-04
i prefer gedit for HTML. just right click on the file, then click "Open With..." then open with text editor. 
This works with HTML, PHP, CSS, C++, Java, Javascript, XML, C, Python, and just about anything else

---

### Post by jrev on 2009-10-04
Thank you all.

I got my solution by suppressing a block of code such as this one : > <tr height=17 style='height:12.75pt'>

  <td height=17 class=xl6729385 style='height:12.75pt'></td>

  <td class=xl8929385>&nbsp;</td>

  <td class=xl6729385></td>

  <td class=xl6729385></td>

  <td class=xl7429385></td>

  <td class=xl9029385>&nbsp;</td>

 </tr>

for each empty line I wanted to suppress in the table

---

### Post by twright on 2009-10-04
> **scragar said:**
> Even in a text editor, if you've got what you're doing mapped out you can make tables layouts much easier than CSS, updating those layouts not so much(because your content winds up everywhere, there's no structure to the code, and every change changes the whole layout, not just the parts you want).
Well I must disagree on this one, with css all you have to do is create a few divs and then apply basic styles where as with tables you have horrible nesting to deal with. Sure tables work well if you are actually creating a table but then why shouldn't they?

---

### Post by scragar on 2009-10-04
> **twright said:**
> Well I must disagree on this one, with css all you have to do is create a few divs and then apply basic styles where as with tables you have horrible nesting to deal with. Sure tables work well if you are actually creating a table but then why shouldn't they?

With tables there's no compatibility issues, which when working with IE is a godsend.

Not saying I agree with anyone making sites using tables, it's a stupid thing to do for the most part, no planning for the future and the updates and changes you'd need to make(and dynamic content with tables = much, much harder).

---

### Post by ad_267 on 2009-10-04
> **scragar said:**
> Tables? Whoever the developer is should be ashamed of themselves.

Dude it was exported from Excel. Tables are the best way to format tabular data...

---

### Post by jlhaslip on 2009-10-05
With a CSS layout, it might be as easy as changing the line-height or margins to reduce the spacing between lines. I am not sure that it would work on a table-based layout since I rarely build a page using tables. Tables are for displaying tabular data, not structuring html pages.
Glad you got it to work for you.

---

### Post by Paqman on 2009-10-05
> **scragar said:**
> making something with tables is faster than making it with CSS

I don't really think it is, except for very basic sites. The lack of flexibility in a table-based layout means you'd be using hacks and kludges right from the start. If you start with CSS, you'd have good clean code.

---

### Post by jrev on 2009-10-05
Thank you Pacman :P

---

