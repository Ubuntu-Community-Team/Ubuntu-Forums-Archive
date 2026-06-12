---
title: "How do I preview separate html files together ?"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by mike101 on 2010-03-13
Hello


I'm new to Ubuntu.

I need to preview html files for a website I'm writing. For each page of the website I have the new content ( on one html file) and 5 "includes" - these are html files which contain the header, footer navigation bar etc.

When I was using windows I had a program which would let me preview these html files together (so I could see the webpage complete with header , footer etc and not just the new content).

All of the htmls files (new content and "includes" are stored in one folder.  

I'd be grateful if anyone knows how to do this this,

Cheers
Mike

---

### Post by coldraven on 2010-03-13
Have a look at open source alternatives at [http://www.osalt.com/web-development](http://www.osalt.com/web-development)
Or maybe Bluefish from the repository.
I have not tried any so I don't know which one is right for you.

---

### Post by spectralblue on 2010-03-13
> **mike101 said:**
> Hello


I'm new to Ubuntu.

I need to preview html files for a website I'm writing. For each page of the website I have the new content ( on one html file) and 5 "includes" - these are html files which contain the header, footer navigation bar etc.

When I was using windows I had a program which would let me preview these html files together (so I could see the webpage complete with header , footer etc and not just the new content).

All of the htmls files (new content and "includes" are stored in one folder.  

I'd be grateful if anyone knows how to do this this,

Cheers
Mike

Hi Mike,

So you have 6 HTML files altogether, 1 of them would be the new content and the other 5 are the navigation and headers and footers right?

How do they come together? How did you do that previously? There should be another HTML file that would bring all these 6 HTML pages together.

It sounds like you want to use <frames> or <iframes> to bring these together. I usually write these codes by hand, or when I design sites, I use Photoshop to get the coordinates. I don't really use an HTML editor when it comes to frames/iframes, because in my experience, they never display properly when it comes to those elements.

---

### Post by era86 on 2010-03-13
Sounds like you had template using Dreamweaver or MS Visual Web Dev.  Like spectralblue said, you should be combining those files in a single HTML using some sort of <frame> or web framework.

Several templating languages exist for this specific purpose.  What did you use to develop in Windows?

---

### Post by mike101 on 2010-03-14
Hello

thanks for your replies

Yes I have six html files in 1 folder. And I want to display these together.

I have been using an editor called Arachnohphilia 

 [http://www.arachnoid.com/arachnophilia/](http://www.arachnoid.com/arachnophilia/)

 but needed  another program called SBI valet 

[http://www.sbi-mall.com/sbi-valet/](http://www.sbi-mall.com/sbi-valet/)

to preview the html files together like this.


I'm wondering if it would be possible to preview  several html files like this with another html editor?  

 Thanks in advance
MIke

---

### Post by mike101 on 2010-03-14
> **era86 said:**
> Sounds like you had template using Dreamweaver or MS Visual Web Dev.  Like spectralblue said, you should be combining those files in a single HTML using some sort of <frame> or web framework.

Several templating languages exist for this specific purpose.  What did you use to develop in Windows?

Hello

I've used a small ready-made program to do this ( SBI Valet).  I don't have any knowledge of templating languages. I'm really looking for a simple solution;) Perhaps some software that is already set up to do this. 

Or otherwise some other fairly straightforward solution.

Any help most welcome....

---

### Post by spectralblue on 2010-03-19
Ah... I see what you mean. SBI Valet does preview several HTML pages at once. But it still does not bring those pages together right? If you can bring all the pages together using <frames>, you only need to open one file on your browser, and it will display all the pages together. Then just hit refresh if you make any changes. I would highly recommend learning a little bit of HTML if you are starting up websites. w3schools.com is a great site for learning HTML, step by step.

Here's a specific section on frames:

[http://www.w3schools.com/HTML/html_frames.asp](http://www.w3schools.com/HTML/html_frames.asp)

---

