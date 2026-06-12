---
title: "Want to copy the website content by using wget."
date: 2010-02-12
forum: New to Ubuntu
---

### Post by nos09 on 2010-02-12
Hey, i want to copy the whole website contents or say want to copy the whole site if possible. 

I've used the wget in terminal and it copied the website but I cant find the things I want.

let's  say I want to copy this site for my personal use     "http://lyrics.astraweb.com/"         the site is for lyrics as u can see.
I did tried this command " 
"wget -r -l0 --no-parent http://lyrics.astraweb.com"
 and 
" "wget - -l0 --no-parent http://lyrics.astraweb.com/browse/band/33/Greenday.html"
and I m not able to copy the all lyrics but the lyrics I've accessed on the web online. so help me to copy all the contents. 

thanks for help in advance. and sorry for the english :(
I m crazy though.:guitar:

---

### Post by Enigmapond on 2010-02-12
That would be much easier to do with just installing httrack. This will copy a website or just rip the things you want. It works very well.

---

### Post by nos09 on 2010-02-12
what is httrack?
and are you sure that i can able to copy the lyrics as well. i dont mid if they are in html form. and i think you should visite the site first just to conform what I'm saying. and thanks for quick replay..

---

### Post by Enigmapond on 2010-02-12
It copies the entire site and makes it browsable offline...copies everything on it. I just tried it and it works...it makes a mirror of the site. You can copy everything or just specific things depending on how you set it up...

---

### Post by nos09 on 2010-02-12
one last question:: 

is there any option for making it continue on next session. i mean guess if the site is little too big to copy at once then can i continue to copy it on next day.???

---

### Post by Enigmapond on 2010-02-12
I'm not sure...never had to do it that way but you can filter out what you don't want and just download, for example just the html pages ignoring all the ads and images...best thing to tell you to do is install it with the documentation and play with it...

---

### Post by kellemes on 2010-02-12
> **nos09 said:**
> one last question:: 

is there any option for making it continue on next session. i mean guess if the site is little too big to copy at once then can i continue to copy it on next day.???

From "step 3" in the httrack-webscreen you can choose "Continue interrupted download" as action.
I guess this is what you want?

---

### Post by nos09 on 2010-02-12
now I tried to copy the url : http://lyrics.astraweb.com/browse/bands/33/Greenday.html" 

without any problem but when i go offline and then openthe html page i just work with only one perticular page. i want the links too work for me. I mean when i click on one of the links then it shows connection error that mean i m offline,

but thats what i want i want to see offline pages. now any one who wants to help me please try it by yourself first. try to copy all the contens and try to make links working..

please.....

---

### Post by Satoru-san on 2010-02-12
There is a feature that will copy recursivly, but you have to be careful, if you try to download a forum, you are looking at infinite downloading not just because of the thread, but because of the calender, I tried downloading a forum one time, and I let it go for a few hours, and when I came back I noticed that it had downloaded like 2 gigs of calenders. You also have to watch out for links off site, especially if they link to google, or it will never stop, though I haven't used this program in a long time and you may be able to restrict downloading to only that domain. Don't quote me on any of that though, I am only speculating.

---

### Post by nos09 on 2010-02-12
found a way ....
I cant copy the whole site though but can copy the artist i want 
for example if i want to copy all the lyrics from greenday band then i will go to the internet page "http://lyrics.astraweb.com/browse/bands/33/Greenday.html" and copy the url then open the terminal and type

> wget -mkE "http://lyrics.astraweb.com/browse/bands/33/Greenday.html"

it will download all the lyrics in indiviual html pages. but the problem is it won't stop untill it will download the whole site. so keep an eye on terminal process and close as it goes on other links,

any other solution are most welcome this wasn't good enough. but can do the trick temporery.

---

