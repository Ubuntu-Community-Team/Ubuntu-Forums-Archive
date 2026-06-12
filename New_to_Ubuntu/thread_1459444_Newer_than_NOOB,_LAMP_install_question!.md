---
title: "Newer than NOOB, LAMP install question!"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by Kellemora on 2010-04-21
Hi Gang

I'm back with more "I'm Totally Lost Here" questions!

I have a spare computer that Lucid won't work on, loaded Hardy which works fine.  Zero Problems...

OK, I have an ancient personal web page that I've had to update a few times to keep it working and would like to polish it up and use it as a learning tool as well.

Decided to stick my 62 year old NOSE into CSS and also a little PHP....
BUT, I don't want to go LIVE with it, just run it for testing purposes on MY OWN in-house web server as a learning tool.

Need to install LAMP, which I know is Linux Apache MySql PHP......
MySql is already loaded.  But WHICH Apache from Synaptic do I use?
Apache 2 or Apache 2.2 Common?????
AND which of the hundreds of PHP files listed there do I need.

I'm just learning PHP so am on page one, print "Hello World" or echo "Hello World"  so only need the basic LAMP structure.

And one really DUMB question.  If I have an .html page that I embed a PHP code to show the date and time, does the ENTIRE .html file need to be saved as a .php file in order to work.  That's where I'm actually stuck at right now!  There may be another way to do this, which I'm sure I will learn now that I have my nose back into html and beginning to study CSS.

Thanks!

TTUL
Gary

---

### Post by P4man on 2010-04-21
[http://lmgtfy.com/?q=ubuntu+lamp+install](http://lmgtfy.com/?q=ubuntu+lamp+install)

First hit:
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

> 
And one really DUMB question. If I have an .html page that I embed a PHP code to show the date and time, does the ENTIRE .html file need to be saved as a .php file in order to work. 

Yes. But that wont work until you have apache and php up and running

---

### Post by Kellemora on 2010-04-21
Hi P4MAN

Now I really feel STUPID!
I've already done all that from that page!

If I type [http://localhost](http://localhost) I get the IT WORKS! page, but NOT the folder they said I would get.

If I type [http://localhost/testphp.php](http://localhost/testphp.php) I get this very long purple file titled PHP Version 5.2.4-2ubuntu5.10 with a php logo to the right.  Which to me means it's working?

I DID NOT do the (optional) part of MySql setup assigning MY IP number, mainly because I wouldn't have any idea what it will be on a multi-computer system, nor do other computers need to access it.

Here is a most simple code:
Perhaps I'm doing something wrong here?
```

<html>
<head> </head>
<body>
<?php
echo 'Hello World':
?>
</body>
</html>

```

Also tried echo Hello World; and echo "Hello World";

As I said, I'm on page one, first paragraph, hi hi.......
And obviously I'm missing something here.  Or my book forgot to mention something important.

I open Firefox Open the file and nada.
If I open other files this same way, I see what I expect to see.

I'm marking this question solved as apparently I have all the items my question asked about already installed and working.

Thanks for your help!

TTUL
Gary

---

### Post by P4man on 2010-04-21
I suppose you are putting the php file in the wrong folder. Are you putting them in /var/www ? i dont quite recall where to put the PHP files, but thats probably your only issue. maybe someone else can chime in, its been a while since I played with it.

---

### Post by P4man on 2010-04-21
oh hang on, you do NOT open a php file directly in firefox! You must request it to the apache server so the php code gets exectuted before it loads in firefox. So you have to open the address [http://localhost/nameofyourphpfile.php](http://localhost/nameofyourphpfile.php) where nameofyourphpfile.php is in the correct apache folder (I think /var/wwwroot or something, but im not entirely sure and its definately a folder you dont have write access to without changing it).

---

### Post by Kellemora on 2010-04-21
Thanks

In rereading my booklet, it DOES say to save the file under my "Web Server Document Root".......

I honestly have NO IDEA what that means!!!!!

I have a SEPARATE /home folder on my filesystem where I keep all of my non-system data, settings and personal & business files, including my web page stuff.

I really don't want to SAVE data in the system folders instead of the /home folder where it belongs.

I look up at the top in the bar of this browswer and almost every page in these forums is something or other.php, I wouldn't think they would be saving all this stuff inside the system folders?

As I said, I'm really MISSING something here!

I'll try using localhost to get to the file and see if that produces any results.  ALL of the tutorials I've picked up on html, css and php all start with the basic or equivalent thereof, of Hello World.  
Until I get past the point of being able to SEE this on my screen when it's run in a web browser, I'm totally lost, hi hi....

Firefox ASKS for a Helper Application if I just click on the file.php
Does nothing if I click on the file.html except printout the html text that says Test Page.....

I wish the books and tutorials were more clear!
They are GREAT all the way through, except for page 1 line 1, Turn on Computer, hi hi.........  In other words, they assume you already know more than I have an inkling about.

But you have given me some GREAT pointers, so thank you!

TTUL
Gary

---

### Post by Kellemora on 2010-04-21
AHA, the error message may be of some help here.

The FILE.php was NOT found on THIS SERVER!

So apparently, there is someplace in my computer now where the server resides, and that's where files need to go.

I wonder where it is?????

Back to the Server Books I guess!

Thanks

TTUL
Gary

---

### Post by Untitled_No4 on 2010-04-21
Your server's Document Root is /var/www (unless the HOWTO you followed specifically said to change it. This is not where the server itself resides but rather where the server looks for files to serve.

I haven't read the HOWTO you followed so I don't know what it says to, but if you get the php configuration then it means both Apache and PHP are running. Try to follow this:

1. Create a file called index.php under /var/www.
2. Open the file with gedit or your favourite text editor and type your code there (the one with <?php echo "Hello world"; ?> and save it.
3. Check that there is no index.html or index.htm files under /var/www. If there are, either delete them or change their name from index to whatever you fancy.
4. Open Firefox and in the address bar type [http://localhost](http://localhost) and press enter.

You should now be able to see your Hello world text. You can then change the text from "Hello world" to something else, save the file and refresh the page. 

Also, anything between the <?php and ?> tags is passed by Apache to the PHP engine to parse. You can echo all your html between those tags but this is unnecessary and inefficient. You can have several <?php and ?> tags in one document if you need.

I hope this helps.

---

### Post by P4man on 2010-04-21
> **Untitled_No4 said:**
> 
1. Create a file called index.php under /var/www.

By default you dont have write permission on that folder, its owned by root. Which makes sense on a production webserver, but not so much when testing stuff, so you may want to take ownership of that folder (or reconfigure apache to a different web root, like /home/yourname/phptestfiles or something and obviously put the php files in that folder.

---

### Post by Kellemora on 2010-04-21
Thanks #4

I'm beginning to remember a few things now also from the rusty old noggin!

Naturally a real ISP or website would not have their thousands of pages stuck there under var/www, wouldn't work for an ISP anyhow, they would need a www folder for each client.

In any case, yes there is an index.html shown there, the one that says "It Works"......
And of course the file "testphp.php" from the LAMP install directions.

I just created a file test.php with my Hello World code it in and it WORKS NOW.

I only have one question left, that I don't quite understand yet and have not found it in the books I'm reading.

If an html document, such as your Index.html used on all ISP's has any php code in it at all, do you RENAME the file Index.php or leave it as Index.html......  I will experiment with this in a little bit to learn on my own.  Sticks better that way, hi hi.....
But web browsers, when you connect to a website, I thought always looked for Index.html and everything else stems from that.

Also I will experiment with a symlink from /var/www to /home/myself/wwwpages or something similar.  There has got to be a way of keeping user data OUT of the SYSTEM area of the computer.

And you have to go to ROOT in order to copy test.php from where it was into /var/www/test.php  Can't just copy and paste to there!

I already know a little (very little) html, trying to clean up my existing web pages some with CSS which I'm just learning as well.
Things we used in html to achieve certain goals are not Kosher!  CSS does it easily and properly.

Thanks for your help!

TTUL
Gary

---

### Post by Untitled_No4 on 2010-04-21
ISPs use Virtual Hosts on shared accounts. Every account has it's own directory on the server and depending on the URL requested it knows where to fetch the files from.

The php extension is what tells Apache to pass the files to the PHP parser. If you change the extension of a php file to html it will just output everything as you typed it in the file and not parse everything.

Apache looks for index.html but if it doesn't find one but finds index.php instead it uses that as the "default" file.

/var/www is pretty standard location for web pages. You can change Apache configuration files to point DocumentRoot to a different folder if you so wish, or you can just as well create a www folder in home folder and then create a symlink under /var/, that will work. 

I usually change the permissions of my /var/www folder on my machines since I they are inaccessible from the outside world and I forgot it requires root permissions by default, sorry for that.

If I also add something that doesn't really answer any of your questions, I'd suggest installing the following addons in Firefox since they will help you learning (and debugging) your code:
Web Developer Toolbar: [https://addons.mozilla.org/en-US/firefox/addon/60](https://addons.mozilla.org/en-US/firefox/addon/60)
Firebug: [https://addons.mozilla.org/en-US/firefox/addon/1843](https://addons.mozilla.org/en-US/firefox/addon/1843)
Html Validator: [http://users.skynet.be/mgueury/mozilla/](http://users.skynet.be/mgueury/mozilla/)

---

### Post by Kellemora on 2010-04-21
Thank you once again #4 those add-on's will come in most handy I'm sure.

html has come a long way since I first built my meager home web pages.
There was a lot I wanted to do back then, but it was basically impossible.
Was stuck in a box so to speak!
Other than minor maintenance, every time I wanted to make a change, I had to learn everything all over again, as lack of usage I forget things easily.

Got a small taste of CSS as how it could really polish things up nicely and make pages appear the same on virtually any web browser.

Ironically, wanting to learn PHP came about because I wanted to show date and time and log it, plus perhaps have a log-in script to get to certain hidden pages.  This will probably be a long ways off yet.  But it never hurts to learn new stuff, especially as you get older, helps keep your mind sharp.

Again, thanks for all your help!
I've got my test pages all working great, and will have to crack a few beginner Linux books again to remember how to use Root to create folders and the like.  Amazing how much one forgets!
Should I BLAME it on UBUNTU?  It's so turn-key now, I just install and go!
Even partitioning is GUI point n click!

TTUL
Gary

---

