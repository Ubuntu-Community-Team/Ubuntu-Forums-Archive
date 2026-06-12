---
title: "file search utility program, catfish??"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by goodbye-windows(tm) on 2011-08-08
Hi All,

Am new to Xubuntu, I hope this isn't a silly question::>

I found the catfish program, whilh allows searches of the various drives in my system and it works well-but....

When I locate a particular file with a catfish search, there appears to be no way to select the file in order to move it, copy it or do anything at all with the file. Yes, I can click on the filename in the catfish output on the screen, and the appropriate application does open the file. 

But, how do I delete it or move it to another folder?

Is there a different program that is used for searching and managing files..or is catfish the only program that ships with Xubuntu?

I'm running Xubuntu 11.04.

TIA

Art

---

### Post by cavh on 2011-08-08
Does this happen (a) on all files or (b) just files that are outside of your home folder? If (b), it's likely to be a file permissions problem. If (a), sorry: I can't help as I don't run Catfish.

---

### Post by Praveen30 on 2011-08-08
you have asked for other applications..hoping this may help you..
[http://http://www.tricksfind.in/2011/05/how-to-search-for-applications-in.html]("http://http//www.tricksfind.in/2011/05/how-to-search-for-applications-in.html")

---

### Post by XubuRoxMySox on 2011-08-08
I have used catfish only to *locate* files, but when I want to move them around or whatever I use a file *manager*. The default in Xubuntu is Thunar, but I discovered a really awesome one during my flirtation with LXDE, called PCManFM. 

-Robin

---

### Post by goodbye-windows(tm) on 2011-08-08
------------------------------
 
  
         For cavh:
 
  
         Catfish finds the file(s) just fine. But, I  can't select a file from the catfish search results and move it, copy it  or delete it. My expectation was that I could drag and drop file(s)  from the catfish screen into another folder.
 
  
         I just finished testing, and it doesn't matter  whether the file originates from the desktop or from the external  expansion drive.
 
  
         In other words, if the file I want to move,  delete or copy is on the desktop, I can't select it and manipulate it.  And, if the file I want to move, delete or copy is on the expansion  drive, I can't select it and manipulate it.
 
  
         So, it is not likely a permissions issue.
 
  
         ------------------------------
 
  
         For Proven30:
 
  
         I hope I don&#8217;t have to find a different application. I&#8217;d like to  try to make the stock software work first-then I&#8217;ll consider adding a  different application if necessary.
 

         ------------------------------
 
  
         For Robin:
 
  
         I am trying to sort and categorize my music  collection, so I have about 11,000 mp3 files in 5 or 6 folders, all of  which are located on my USB based expansion drive). Obviously, manually  searching that many files using the file manager will be very slow. 

 
  
         So, I open catfish, and give it search  parameters and tell it to &#8216;find'. It returns a list of tunes which  include the desired file. 

 
  
         After the file is located, I assume I can click  on the catfish screen to select the file, and then drag and drop  directly from the catfish screen. But, when I click on the file I want  to move/copy/delete, there appears to be no option to do anything with  the file.
 
  
         When you find the file you&#8217;re interested in  moving around (using catfish), how do you go about telling the system  manager to move/copy/delete that file????
 
  
         In other words, you&#8217;re looking at the catfish  screen that shows multiple files that meet the seach criteria. And lets  say the third item in the list on the catfish screen is the file you&#8217;re  interested in manipulating. Exactly which keystrokes/mouse commands do  you use to go from catfish in order to instruct the file manager to do  the desired manipulating?
 
  
         Here&#8217;s what I am expecting catfish to do.....
 
  
         After the file is located using catfish, I move  the mouse over the catfish screen and left click on the file I&#8217;m  interested in moving (a single click, without releasing the mouse). The  cursor changes to a &#8216;copy&#8217; cursor and I drag and drop the file from the  catfish screen to the desired folder. Once the cursor is over the  desired folder, I release the left mouse switch and the file should be  copied to the desired folder.
 
  
         What happens on my system however, is that the  cursor never changes to the &#8216;copy&#8217; cursor, and when I hold down the left  hand mouse switch, nothing happens..it does not grab onto the desired  file like it should.
 
  
         It's appears to me like catfish was not  designed to do anything with the desired file (other than to tell the  user the file does exist).
 
  
         [LEFT]------------------------------[/LEFT]

---

### Post by goodbye-windows(tm) on 2011-08-17
Solution is to stop using catfish-catfish does searches well, but after the desired files are located, catfish doesn't allow them to be manipulated.

The answer is to install gnome-utils. It searches and allows the list of files to be selected in part or in whole, and they can be dragged and dropped just as one does in the file manager.

 GL to all.

Art

---

