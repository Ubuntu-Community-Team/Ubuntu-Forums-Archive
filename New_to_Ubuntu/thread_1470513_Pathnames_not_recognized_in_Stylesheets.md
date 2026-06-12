---
title: "Pathnames not recognized in Stylesheets?????"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Kellemora on 2010-05-02
Hi Gang

Have a bit of a problem I've been working on for days now.

Have a handwritten (not generated) html/css file done on Gedit in Hardy LTS, fully W3C validated with 0 errors, 0 warnings.

images called via the CSS are NOT recognized on an Ubuntu local machine running Firefox.  The same script runs perfectly on a local XP machine.

4 different webmasters all using WAMP (Windows) took a look at it and the path coding is perfect. Nonetheless we have tried like a dozen different path options.  Most of them work on the Doze, none work on a local Ubuntu machine.

I know it's hard to know whats going on without seeing the complete files.
But I managed to get it working by installing the images directly into the style folder with the css page, instead of the gfx file where they belong.  Calls from the html file to the gfx folder work just fine!

Here is a line from the CSS that works (with the image in the same folder as the CSS.
```

#header {
     background-image: url('./headercastles3.jpg');
     background-repeat: no-repeat;
}

```

Now, if the image is in the gfx folder where it belongs, and the css stylesheet is in the style folder where it belongs, and the html is in the main directory.  We have to back out of the css style folder into the main directory.  Therefore the proper code to do this is:
```

#header {
     background-image: url('../gfx/'headercastles3.jpg');
     background-repeat: no repeat;
}

```
And yes the html LNK to the stylesheet is correct!

It does not work loaded onto a local Ubuntu LAMP server either!

Having a few other issues as well that work correctly on an XP local machine but fail on an Ubuntu local machine. EG:
```

#index1 {
     font-size: 120%;
     font-weight: bold;
}

```
Works fine!
But the one below does not work at all.
It's called in exactly the same way from the html.
Both are nested within the same level.
```

#index2 {
     font-size: 120%;
     font-weight: bold;
}

```

Just curious if anyone else was having these types of problems?

The script runs properly by others and on the Doze.......

As the webmaster who checked it for me said.
If it works on my machine, and it works on the server, and it works on both of your XP machines, one Pro and one Home, but it doesn't run on your Ubuntu machine.  It's either your Firefox is messed up or your Ubuntu is messed up or not set up right.  The script even runs on a MAC OK too!

Any ideas gang?

TTUL
Gary

---

### Post by _0R10N on 2010-05-02
Well pal, honestly I think that the OS has nothing to do with this. In the case of web development, the OS main task is to host files and the database. The OS of a server doesn't interpret the pages it hosts. It's the web browser job, to render appropriately what is received from the server.
In this case, we're talking about CSS processing, so it's my understanding that no job relating to this, takes place on the server side.
Taking this under consideration, you could try accessing your documents through a different web browser, like Chrome.

---

### Post by Kellemora on 2010-05-03
Hi OR1ON

I realize the OS itself nor a server unless it's php and uses side server script.  But the Web Browsers designed for use on Linux DO work quite a bit differently than those same web browsers on windows.

I know the Firefox I use on Ubuntu Hardy has many more features than the same issue on Windows.

I have a wonderful helper in England/UK that has downloaded my script and passed it around among his colleagues.  They see no errors or anomalies and it runs fine for them.  I move it to a Windows machine, it runs in Firefox on their just fine also.  I used no codes that upset IE or NN, the fixes to get around the bugs in IE upset Chrome, so I felt it best to steer clear of any code that is not recognized across the board.

Nonetheless, the PATHNAME to the file folders (directories) has to be changed to run on a Windows local machine, they use \ where we use /.
But if placed on a server, it really doesn't matter which type of OS draws it as long as the pathnames are valid on the host.

And that is REALLY where I'm stuck at.  On the LOCAL machine, the pathname is invalid when used in the CSS but works fine if used in the html.  And the path is definitely OS related!

TTUL
Gary

---

### Post by Untitled_No4 on 2010-05-03
I'm assuming you link to the CSS file not using the absolute path on the filesystem but either relative to the html file or the document root of the server.

First step, try to browse to the CSS file directly from Firefox and see if it opens the files or if  you get an error. My guess is that it might not have the permissions to allow apache to open the file. But it's a shot in the dark.

Umm, also, I always use an absolute path to the image, so my code would look like that:
```
#header {
     background-image: url('/gfx/'headercastles3.jpg');
     background-repeat: no repeat;
}
```
assuming that gfx is directly under the document root.

EDIT:
Oh, wait, why do you have an extra ' there before the file name? It should read
```
#header {
     background-image: url('/gfx/headercastles3.jpg');
     background-repeat: no repeat;
}
```

---

### Post by _0R10N on 2010-05-03
wow, this is the first time I hear of something like this. I'm a webdeveloper, too, and I never went through such a thing. I strongly recommend you to try with a different browser on your  computer. I will be glad yo help you out if you email me a sample to my msn address.

If you don't feel confident emailing your work, you can attach here a small fragment here.

---

### Post by Kellemora on 2010-05-03
Hi OR1ON

Do you visit Tizag webmasters forum, that's one of the groups trying to figure out the problem for me, both my html and my css are on there.

For Untitled4, that extra ' is just a typo made here.  I typed examples instead of cut n paste.

The html SEES the CSS file just fine, I can make changes in it and they appear just fine in the web browser.

Maybe I didn't explain my problem just right for it to make sense.
We have the following directories:  /home/weblink/newwebsite/...
Within the directory /newwebsite/ are the following sub-directories:
/gfx; /style; /lnkstp; /htmlpgs;

The directory named weblink is a symlink from /var/www/
However, I also have a directory located in /home/gary/desktop/newwebsite
where I do my work, then copy the /newwebsite directory into the /weblink directory for testing.

The index.html page is located in the directory /newwebsite as this is the main directory for the html stuff.
The css stylesheet is located in the directory named /style
The index.html references the stylesheet just fine, no problems there.
The index.html references images placed in the /gfx directory just fine also.

Now, here is where the problem comes in!!!!!
Images called by the stylesheet CAN FIND the images ONLY IF they are placed in the directory named /style and NOT in a sub-directory within the /style folder.  Not that I would want them there anyhow.

Images belong in the directory named /gfx, but the Pathname to that directory has never worked, no matter how many possible variations we have tried.

And yes I DO realize that you must BACK OUT of the /style directory into the /newwebsite directory in order to point to the /gfx directory.
This is done using ../ from the /style directory.  So the line to get TO the /gfx directory should simply be ../gfx/image.jpg or if you want the full code it would be
background-image: url('../gfx/image.jpg');

Now, IF I place the image DIRECTLY into the /style directory, I use the following to call that image and it works just fine.
background-image: url('./image.jpg');

OK, now lets move over to Windows XP-PRO using the SAME folder hierarchy.
I change the css to read the image in the /gfx folder as such:
background-image: url('..\gfx\image.jpg');
Using Firefox on Windows XP-Pro and XP-Home for that matter, the web page displays properly!  All the images called by the css are visible, no problems.

By the same token, I can place the images in the /style folder and they work their too on any Windows machine using either:
background-image: url('.\image.jpg);  OR just
background-image: url('image.jpg);

Now do you see WHY we are pulling our hair out over here?????

The pathname is coded properly!  And the Calls to the CSS are coded properly, else the web page would fail with the images in the /style folder as well......
The FACT that they work when IN the /style folder, but NOT when they are in the /gfx folder tells me, something is NOT reading the pathname properly.  As I said, it works on Windows running Firefox, but NOT on Ubuntu running Firefox.  I've tried it on 4 different Ubuntu machines also, so can rule out a specific computer.

FWIW: the LINK in the html reads properly also, else nothing else would work.
<link rel="stylesheet" type="text/css" media="all" href="./style/webpage.css" />

Except of course if I move it to a windows machine, we change all pathnames from / to \, but NOT the html coding symbols of /> of course!

So even though neither html or css have anything to do with the OS, parsing those pathnames apparently sure does!!!!!

I know enough about CSS to know that their are levels of priority, and if something with a greater power can override a call made by something of a lesser power.  Like if you use the Active Link command ahead of the Hover Link command, the Hover command will be dominate and you won't see the Active Link command.  You can also use this to prevent Visited Links from appearing as Visited by placing the Visited Link at the top of the list, which causes the Unvisited Link below it to dominate.

I have carefully checked my CSS to insure the background-image call is not being dominated by other calls.  Have tried both Class and Id methods as well.

The problem is in the parsing of the Pathname!

In using straight html with no external stylesheet, placing css info in the header works.  Also, placing the stylesheet IN the /main directory works as well to make calls to the /gfx image folder.

So, what it appears to me is that the ../ (double dot slash) is NOT being recognized.  I've tried enclosing the call in double quotes, single quotes, no quotes, tired different forms of coding the call.  Na Da.....

Edited to Add:  We also tried using ../../ to back clear out of both folders and move back forward into /newwebpage/gfx/image/jpg and that didn't work either!

To make matters even more confusing, font-weight changes work in some areas of the css but not others, again no dominant to override the call.

I was hoping someone would know of some bug or glitch that might require a special instruction when using Ubuntu or Apache on Ubuntu.

I've removed CentOS and Debian from my computers since I only use Ubuntu now, so couldn't test it on other OS's other than the Doze.

I figure if 4 different web masters can't find a problem and it runs for them perfectly, WHY doesn't it run on ANY of my Ubuntu machines?????

Thanks for your help!

TTUL
Gary

---

### Post by Untitled_No4 on 2010-05-03
> **Kellemora said:**
> I figure if 4 different web masters can't find a problem and it runs for them perfectly, WHY doesn't it run on ANY of my Ubuntu machines????

4 different webmasters using WAMP... If none of them was using Ubuntu or at least another Linux then it's not very useful since things work differently on Windows beyond just the question of path separators.

I set background images like that all the time and they're never in the same folder and I have never had that issue.

I'll make the same offer _0R10N made for you to email your code to me and I'll try it on my machine. If you don't feel comfortable sending the code you're working on just make a sample html file and a sample css file that don't work for you. The best way would be to archive your /var/www/ folder and send it as it is so the folder structure is preserved. 

Other than that, there's the symlink. If I understand you correctly the document root of your server is /var/www and /home/weblink is a symlink to it, which shouldn't be a problem. However, Apache needs to be told to follow symlinks so maybe there's an issue here.

What I do, by the way is mount my working folder on to /var/www rather than create symlinks since that way I avoid issues with symlinks.

---

### Post by Kellemora on 2010-05-03
Hi U4

Don't think it would have anything to do with Apache, since I'm reading the file directly from my desktop.
But when I DO put it in the symlink folder so I can check it on other computers everything seems to be alright with it.

I'm going to start all over from the beginning again!
There is truth to the old saying, too many cooks spoil the soup.

I had set up my page one way, but was having some problems.  Looked at several web sites to see how they set things up, then talked those things over with a few guys on the webmasters forum.
Ended up making changes to emulate what it appeared the big guns were doing, which was mistake #101 hi hi.......  Then changed things around again to the way they said they should be, so i was just getting in deeper and deeper.

I let a professor take a look at my work, although he said I had the individual components right, I went about it in the wrong way.  What was LOGICAL to me, do the header first, then nav, then content, I forgot to build the house first before moving the furniture in, so to speak.
Although he referred to my working layout as GARBAGE, he said it only needed a couple of things to fix it.
Trouble is, those couple of minor things create a MAJOR overhaul, simply because I cemented the picnic tables in the pavilion to the floor.  So I have to undo all of my glue joints and let thing move around so to speak.

In any case, he seems to think the reason my links are not functioning is simply because you can't heat or cool the great outdoors with a furnace.
You can read that as, I didn't make a Container, because I thought <Body> was the container.  Still don't understand it all, BUT I made a couple of small test html's with stylesheets and the links work on it.

So, it's obviously something I did!!!!!
I'm going to mark this thread solved, since it appears to be Driver Error, hi hi.........

TTUL
Gary

---

