---
title: "How to print a pdf document as booklet ?"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by ubfu on 2009-07-12
I wanted to print a pdf file.Inserting and resize 4 pages into one A4 paper printing front and back.

I can't find anything eventhough at window , I can find a right software/application can do that.

Printing 4 pages resize it at the front page 1 , 3 ,5 , 7
and back page 2 , 4, 6, 8 

where 2 page is the back of 1 , 3 is the back of 4 , 5 is the back of 6 and 7 is the back of 8.
I don't know how to explain in word , there I attach a example on how I wanted it to print out.

Thank you , hope someone can guide me how to print it and sorting it as order

---

### Post by ubfu on 2009-07-14
Any help please ? 
Thank you

---

### Post by ramnarayan on 2009-07-14
> **ubfu said:**
> I wanted to print a pdf file.Inserting and resize 4 pages into one A4 paper printing front and back.
snipped >
Thank you , hope someone can guide me how to print it and sorting it as order

Much as i would like to say nice things about Linux - there is no easy solution to this . In fact the only solutions are a pain in the *** and it may be better to look for an alternative.

Saying that 
1. Depending on that you could first split your pdf file into single pages using pdftk (command line) or pdf sam(i have never used this)

then do a mock up of what you want - 

then order your pages accordingly and then do the 4 per page print 

i am fairly sure this will work because some times (once a year atleast) i have to do something like this and what should take me 10 minutes takes me 10 hours and since inefficient as i am i refuse to use any proprietory software.

***
if it helps i can mail you a spreadsheet that will help you order the pages (you will have to use the spreadsheet suited to your specs)

regards
ram

---

### Post by paparozoumis on 2009-07-14
Sad to say that here but every time I want to do something like that, I use my Windows XP computer where it's really easy to do that. 
There are options there to choose how many pages of your pdf file you want in one printable page and then options of how the printer will handle the pages (front printing first and when it's done with that you flip the pack to do the back printing). 

I'd like to see a similar solution on Ubuntu, though...

---

### Post by ramnarayan on 2009-07-14
post your ? did a quick search to see if any improvements have happened on this front

check out 
[http://www.laidout.org/](http://www.laidout.org/)

seems like the solution we were looking for

---

### Post by ubfu on 2009-07-15
> **ramnarayan said:**
> post your ? did a quick search to see if any improvements have happened on this front

check out 
[http://www.laidout.org/](http://www.laidout.org/)

seems like the solution we were looking for

I install the .deb but it doesn't show any the application icon.
Where does it save ? I can't even find the program that I installed.

---

### Post by ramnarayan on 2009-07-15
> **ubfu said:**
> I install the .deb but it doesn't show any the application icon.
Where does it save ? I can't even find the program that I installed.

ok
i installed to know more about this programme that i suggested to you

so open a terminal and
type laidout and enter it runs the programme
(you could also create a launcher for it by rightclicking on the desktop and going to create launcher)

As to how the programme works i have not gone so far.

Les us know if it works

---

### Post by unutbu on 2009-07-15
Here is an alternative method using the command-line:

Install the poppler-utils and psutils packages.

Open a terminal (Applications>Accessories>Terminal) and run
```

pdftops -nocrop -paper A4 -expand test.pdf test.ps 

```
The above command converts the pdf file (test.pdf) to a postscript file (test.ps). Change the name "test.pdf" to whatever your pdf is actually called.
```

pstops -d "8:0@0.5(0,0.5h)+2@0.5(0.5w,0.5h)+4@0.5(0,0)+6@0.5(0.5w,0),3@0.5(0,0.5h)+1@0.5(0.5w,0.5h)+7@0.5(0,0)+5@0.5(0.5w,0)" test.ps test_booklet.ps
```

The above monster rearranges the pages in the desired order.

If you have a duplex printer (one that can print on both sides), then you are all set. Just print test_booklet.ps.

If you do not have a duplex printer, then you will have to manually print all the odd pages, then flip the pages over, put it back in the printer paper tray, and print all the even pages (in reverse order, since the last odd page is on the top in the paper tray). 

These commands break test_booklet.ps into odd and even pages:
```

pstops "2:0" test_booklet.ps > test_odd.ps
pstops "2:-1" test_booklet.ps > test_even.ps
```

---

### Post by niteshifter on 2009-07-15
Hi,

+1 unutbu's last post. I'll just add this: The OP said print but may want a pdf file of the result so he'll need to:
```
ps2pdf test_booklet.ps test_booklet.pdf
```

---

### Post by ubfu on 2009-07-18
> **unutbu said:**
> Here is an alternative method using the command-line:

Install the poppler-utils and psutils packages.

Open a terminal (Applications>Accessories>Terminal) and run
```

pdftops -nocrop -paper A4 -expand test.pdf test.ps 

```
The above command converts the pdf file (test.pdf) to a postscript file (test.ps). Change the name "test.pdf" to whatever your pdf is actually called.
```

pstops -d "8:0@0.5(0,0.5h)+2@0.5(0.5w,0.5h)+4@0.5(0,0)+6@0.5(0.5w,0),3@0.5(0,0.5h)+1@0.5(0.5w,0.5h)+7@0.5(0,0)+5@0.5(0.5w,0)" test.ps test_booklet.ps
```

The above monster rearranges the pages in the desired order.

If you have a duplex printer (one that can print on both sides), then you are all set. Just print test_booklet.ps.

If you do not have a duplex printer, then you will have to manually print all the odd pages, then flip the pages over, put it back in the printer paper tray, and print all the even pages (in reverse order, since the last odd page is on the top in the paper tray). 

These commands break test_booklet.ps into odd and even pages:
```

pstops "2:0" test_booklet.ps > test_odd.ps
pstops "2:-1" test_booklet.ps > test_even.ps
```

I type 
 pdftops -nocrop -paper A4 -expand /home/user/Desktop/form.pdf form.ps
But no output at all.Nothing showing , the terminal just say normal.What should I do ?
How does the page looks like ? Sorry newbie to ubuntu , I dont know what does the command works.What will the result me ?


> **ramnarayan said:**
> ok
i installed to know more about this programme that i suggested to you

so open a terminal and
type laidout and enter it runs the programme
(you could also create a launcher for it by rightclicking on the desktop and going to create launcher)

As to how the programme works i have not gone so far.

Les us know if it works

Nope it doesn't work.I mean it show the problem but I dont know what to press to work.

---

### Post by unutbu on 2009-07-18
```
pdftops -nocrop -paper A4 -expand /home/user/Desktop/form.pdf form.ps
```

This pdftops command would create the file form.ps in the "current working directory".
When you open a terminal, the current working directory is your home directory: /home/user
So even though the input comes from /home/user/Desktop/form.pdf, the output would be 
/home/user/form.ps.

To view the postscript file form.ps, you could navigate to your home directory using a file browser and then double-click the icon. Clicking Places>Home Folder would take you directly to your home directory, /home/user.

To keep all the files in /home/user/Desktop you could do this instead:

```
cd ~/Desktop     # Change current working directory to /home/user/Desktop
pdftops -nocrop -paper A4 -expand form.pdf form.ps
pstops -d "8:0@0.5(0,0.5h)+2@0.5(0.5w,0.5h)+4@0.5(0,0)+6@0.5(0.5w,0),3@0.5(0,0.5h)+1@0.5(0.5w,0.5h)+7@0.5(0,0)+5@0.5(0.5w,0)" form.ps form_booklet.ps
```

If you do it this way, all the files, form.pdf, form.ps, form_booklet.ps will be in ~/Desktop (and thus will show up on your Desktop too.)

---

### Post by rommelsousa on 2009-09-24
[http://bookletcreator.com](http://bookletcreator.com) does the job.

---

### Post by ubfu on 2009-09-29
Thanks but somehow , the pdf is encrypted where pages can't be arrange.How to enable it to arrange back ?

---

### Post by dox_drum on 2009-10-27
[http://sites.google.com/site/ocastillofelisola/Home/linux-stuff/convertingpsfilesintobooklets](http://sites.google.com/site/ocastillofelisola/Home/linux-stuff/convertingpsfilesintobooklets)

If you have a PS file (from your PDF) use the steps in the link.

[CENTER]Enjoy![/CENTER]

---

### Post by shane2peru on 2010-01-11
I have carefully looked at this a lot as I print books from my linux box.  I stumbled across this thread trying to remember what apps I needed installed.  I have a couple of scripts I use to complete this exact task.  I would need to clean them up a little as they are specific to my system.  They are all bash scripts and I would be more than happy to share them if they are still needed.  Let me know.

Shane

---

### Post by shane2peru on 2010-01-13
Ok, here is my script to print a pdf to a booklet, use it at your own risk :)  It is certainly not perfect, but I have put a lot of time into it for my own use.

```

#!/bin/bash
#This script requires psutils and poppler-utils install them with sudo apt-get install poppler-utils psutils
echo "You may need to review the -b option on line 34ish of this script" 
sleep 5
#read -p "What book do you want to convert and print (you don't need the pdf extension)?     " book
book=$1
read -p "How many pages do you want to print? multiples of 8 are best, 16, 32, 64 (64 will print 16 pieces of paper) ...    "    p
#read -p "Page numbers to print?   " pages
read -p "What printer default press enter, for PDF type PDF:   "  printer
######################
#Skip dark first page#

######################
read -p "What page should we start at?    "  f
###################################

rm -f $book/*.ps

####################
#Variables declared#
####################

s=1
l=$p
if [ l gt 1 ]; then l=$p
else l=$((f+$p-1))
fi
mkdir $book

#####################################
#Functions should go in this section#
#####################################

function pagerun {
	psnup -l -pA4 -2 -b1 $book/$book-temp$s.ps > $book/book$s.ps #-s don't use this option, offsets page centering if the page is too large  add or edit the -m number option margin, set the margin for the whole page in cm or -b for border around each page also in cm.  The Border option is probably the best as it also adds a margin.
	pstops "2:0" $book/book$s.ps > $book/$book-odd$s.ps
	pstops "2:-1" $book/book$s.ps > $book/$book-even$s.ps #optional config: (0in,-0.335in)
	read -p "Ready to send to printer?" enter 
	lpr -P $printer -o media=A4 $book/$book-odd$s.ps
	echo "Printing $book/$book-odd$s pages with - lpr -o media=A4 $book/$book-odd$s.ps"
	read -p "Re-insert pages and press enter" enter 
	lpr -P $printer -o media=A4 $book/$book-even$s.ps
	#lpr -o media=A4 $book/$book-even$s.ps
	echo "Printing $book/$book-even$s pages with - lpr -o media=A4 $book/$book-even$s.ps"
	echo .
	echo .
	read -p "To print next set press enter" enter
	echo .
	echo .
	s=$((s+1))
}

function cleanup {
	read -p "Did all the sets print correctly?  y/n   " ans
	if [ "$ans" = "y" ] ; then rm -rv $book
	else
	exit
	fi
	exit
}

function selectpage {
	psselect -p$((l+1))-$((l+$p)) $book/$book.ps | psbook > $book/$book-temp$s.ps
	l=$((l+$p))
echo $l
}

function repeat {
	if [ $pcount -lt $l ] ; then echo "we are at page $l" 
	cleanup 
	else
	echo "we are at page $l"
	selectpage
	pagerun
	fi
}

clear
echo "Converting book to post script"
pdftops -nocrop -paper A4 -expand $book.pdf $book/$book.ps  
pcount=$(grep -c %%Page: $book/$book.ps)
echo "$book has $pcount pages"

##  Sending the book to the printer!
psselect -p$f-$l $book/$book.ps | psbook > $book/$book-temp$s.ps 
pagerun

###  Right here is where I should be able to loop this and avoid the repetition.
echo "starting the loop section"

while [ $pcount -gt $l ]
	do
		repeat
	if [ $pcount -lt $l ]
	then cleanup
	fi
done
cleanup

exit


```

You will need to know the name of your printer you can find that out with ```

lpstat -a

```
You will need to type that as it is shown in that dialogue.  I'm sure there are room for improvements, but it works for me.  Questions?  Just ask and I will try to help as time permits.  

To use it you need to name it something I used printbook5 (I'm up to revision 5) it needs to be in your path and it can be used like this:
```

printbook filename

```
leave off the .pdf or it will not work. :)  This will only print pdf files.  You must have psutils and poppler-utils installed.

```

sudo apt-get install psutils poppler-utils
```

Shane

PS  -  I often print to PDF as my printer first to test the file and see how it will look to not waste paper and ink, the files are then found in your HOME directory under PDF folder.

---

### Post by ubfu on 2010-01-13
Thanks for the script :D;), but need some help guiding how to use the script , sorry newbie .
What if I wanted to print from left to right ?

---

### Post by shane2peru on 2010-01-13
Copy the script from above and paste it into a a text editor (Applications -> Accessories -> gedit)  and save it as printbook5 in the same folder as your pdf file to make it easier for you.  Open up the terminal (Applications -> Accessories -> Terminal)  and navigate to where you saved this stuff with ```
cd location/of/file
```  and then type or paste this:```
chmod +x printbook5 && lpstat -a
```
The first part is going to make the script executable and the second is going to give you your printer name.  Now run ```
./printbook5 filenameofpdf
```  You don't need the .pdf part.  It will ask you how many pages you want to print, I cut them and bind them, however if you want a booklet to be folded and stapled, you need to select a large number so it prints them all at one shot.  Next it will ask you for the printer, use PDF first (capitol letters) if it shows up in your lpstat -a results.  If not use the printer name that you want to print on. It will print one side and then have you flip the papers and print the next set.  At the end it will remove the temporary files it made.  It isn't a user friendly script as I made it for myself.  Good luck using it.

Shane

---

### Post by ramnarayan on 2010-01-14
[QUOTE=shane2peru;8657227]Ok, here is my script to print a pdf to a booklet, use it at your own risk :)  It is certainly not perfect, but I have put a lot of time into it for my own use.

Hi Shane from Peru

Thanks

Whats exciting is not just the script but the fact that i am also able to get it from some one using Ubuntu on another high mountain range :-)

thanks

ram

---

### Post by kavoura on 2012-01-05
I use Adobe Acrobat in Ubuntu, works okay for me when doing booklet printing. I know it is not FOSS, but sometimes things like Acrobat are just what is needed when no FOSS alternative exists.

---

### Post by oldos2er on 2012-01-05
Closed, necromancy.

---

