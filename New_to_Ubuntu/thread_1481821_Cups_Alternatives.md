---
title: "Cups Alternatives"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by expatCM on 2010-05-13
What are the alternative solutions to cups for network printing?

A problem has appeared in cups which means that I cannot print graphics (like a ,jpg) on either of the printers connected to the server.  I can print .txt, .doc, .pdf.  I cannot solve this problem.  Not even after reinstalling cups and playing with a multiplicity of drivers.

So I need an alternative.  Any suggestions?   


I get an error of "/usr/lib/cups/filter/pstoraster failed" or the job simply disappears.  The log file does not seem to make a lot of sense.  So many others have this type of problem but there appears to be no solution.  Most threads posted are not answered ... 

```
[Job 18] Error: /limitcheck in --array--
D [13/May/2010:10:35:57 +0700] [Job 18] Operand stack:
D [13/May/2010:10:35:57 +0700] [Job 18] 70264
D [13/May/2010:10:35:57 +0700] [Job 18] Execution stack:
E [13/May/2010:10:35:57 +0700] PID 9582 (/usr/lib/cups/filter/pstoraster) stopped with status 1!
D [13/May/2010:10:35:57 +0700] PID 9584 (/opt/OpenPrinting-Gutenprint/cups/lib/filter/rastertogutenprint.5.2) exited with no errors.
D [13/May/2010:10:35:57 +0700] [Job 18] %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1905   1   3   %oparray_pop   1904   1   3   %oparray_pop   1888   1   3   %oparray_pop   1771   1   3   %oparray_pop   --nostringval--   %errorexec_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--
D [13/May/2010:10:35:57 +0700] [Job 18] Dictionary stack:
D [13/May/2010:10:35:57 +0700] [Job 18] --dict:1152/1684(ro)(G)--   --dict:0/20(G)--   --dict:93/200(L)--   --dict:66/75(L)--
D [13/May/2010:10:35:57 +0700] [Job 18] Current allocation mode is local
D [13/May/2010:10:35:57 +0700] [Job 18] Last OS error: 2
D [13/May/2010:10:35:57 +0700] [Job 18] GPL Ghostscript 8.62: Unrecoverable error, exit code 1
D [13/May/2010:10:35:57 +0700] [Job 18] Gutenprint: About to start printing loop.
D [13/May/2010:10:35:57 +0700] [Job 18] Gutenprint: Printed total 0 bytes

```

---

### Post by srs5694 on 2010-05-13
You could try LPRng; however, switching out CUPS for LPRng just because you can't print JPEGs is likely to be the harder solution. The easier one is to find a way to print the JPEGs via CUPS. You don't say how you're currently trying to do this. If it's to print directly (e.g., "lpr foo.jpg"), then you could try converting from JPEG to PostScript or some other format, say using [jpeg2eps](http://rses.anu.edu.au/~andy/jpeg2eps/) or something similar. Alternatively, you could load the JPEG into the GIMP, [xv,](http://w140.com/kurt/installing_xv_in_ubuntu.html) or some other graphics program and use its print function.

---

### Post by expatCM on 2010-05-14
I may understand what the real problem is now.  I post this message so that others can read my error, Google tells me that there are many many people with the same sort of challenges but they ask and there is rarely a reply and never a solution.

Open the job with Image Viewer (or Gimp) and it does not print. Sometimes I get a message "Printing - not connected?" in the print queue.  The cups printer information gives "/usr/lib/cups/filter/pstoraster failed" for the same event.  Really not helpful.  So I played around with different drivers and saw an error message (in the error log) I had not seen before.   It was "PostScript error: limitcheck".  So I looked it up.  What it seems to mean is that either the printer(s) have insufficient memory for the job being printed or the resolution of the image is too great. This link is very helpful.
[http://www.prepressure.com/postscript/troubleshooting/errors/limitcheck](http://www.prepressure.com/postscript/troubleshooting/errors/limitcheck)

Whist I had tested with different images and had checked the file size (about 465KB) I had not considered the pixel resolution which in this case is all photos are 4000 x 3000.   So what probably is happening is that the print job is simply too large for the printers to handle.  In turn that is why I could see one printer flashing to accept the job and then give up (since it has 8MB of memory).

I now need to test this properly just to be certain that I have this right.  I also need to work out how an easy way of scaling these images for daily printing ....

I also need to work out how to fix my adventures in cups.  When I now delete all printers and restart cups with a view to setting up fresh I get a choice of three versions of the same printer.  I guess this may be due to the range of drivers I now have installed but it is not so easy to know what to select.

---

### Post by srs5694 on 2010-05-14
If you need more help on this, you need to provide information on your printer -- its model and whether or not it's a PostScript model. Information on its CUPS configuration is also required. Some background:

In Linux printing, programs assume that every printer is a PostScript printer. (There are some exceptions to this rule, but for the most part it holds.) That is, programs produce PostScript output and send it to the printing system (normally CUPS these days). The printing system (CUPS), though, knows better, so it converts the file from PostScript into a form that the printer can understand. If the printer is a PostScript printer, then no conversion is necessary; but if the printer is not a PostScript model, the file must be converted. CUPS does this conversion with the help of Ghostscript, which is a PostScript interpreter that runs on the computer rather than on the printer. The CUPS "driver" is actually a set of rules for how to call Ghostscript to do the conversion.

I'm far from an expert on PostScript; however, the reference you provided indicates that the limitcheck error is a PostScript error. This means that it might be an error in the printer itself *or* in Ghostscript, depending on the type of printer you've got and how you're using it. If the printer is a PostScript model and if it's producing the error, perhaps increasing its RAM would help. If you're using a non-PostScript printer (or a non-PostScript driver for it in CUPS), perhaps using another driver or tweaking driver settings would help. If the printer is a model that supports both PostScript and non-PostScript modes of operation, perhaps switching from one mode to the other would help. In all cases, perhaps changing options in the printing application would help (to change the PostScript level generated by the program, for instance, or changing the resolution settings).

As you can see, there are a lot of possibilities here, and to narrow them down, much more information is required, starting with basic details of your printer hardware and what drivers you're using in CUPS.

---

### Post by expatCM on 2010-05-14
Thank you for your latest post.  There is a lot of information there and for me it is certainly helpful information.  Thanks again.

At present everything is working as I need and so I really want to leave it be.  In understanding this problem I have gone into cups at much deeper levels than I ever anticipated and I nearly drowned in the information.  Since my neck is now out of the water I want to move on to other challenges.

---

