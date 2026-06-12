---
title: "use open office spread sheet for darts application"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by LTFC2020 on 2009-04-13
I know this may not be the best place to pose this question but having done a google search maybe this is a good starting point
I would like to use the open office application to create a darts scoring system
I have searched the linux sites for a similar application with no luck and have also used the openoffice help files but as I am so unfamilar with this type of application that i have just ended up confused (default setting)
my question is this:
does anyone know of either a program or simple way of getting open office spreadsheet to subtract any number from 501 as and when the user inputs a number
thanks in advance for helping an ubuntu fan with no spreadsheet knowledge

---

### Post by Sir Jasper on 2009-04-13
Hi,

(1) Type 501 into cell B1 and press enter.
(2) Type =B1-A2 into B2 and enter
(3) With the cursor on B2 right click and select Copy
(4) Move the cursor to B3 left click and drag down down to say B50
(5) Release the left click then right click and select Paste
(6) Type your fist 3 dart score into A2 and enter
(7) Type your second throw total into A3 and enter, etc, etc

If you have an opponent just use two more columns in a similar way.

When the game is over Copy the Blank Space in A1 down column A to clear everything below.

Say you score treble 19 + 20 + double top (by accident) with your first throw you could type =57+20+40 into cell A2.

This is the simplest and most basic example.

My regards

---

### Post by LTFC2020 on 2009-04-14
fantastic
thanks a lot sir jasper

---

