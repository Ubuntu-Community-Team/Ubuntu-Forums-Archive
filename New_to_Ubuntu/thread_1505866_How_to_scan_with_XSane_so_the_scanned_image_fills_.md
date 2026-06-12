---
title: "How to scan with XSane so the scanned image fills a standard 8 1/2 x 11 page?"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by swarup on 2010-06-09
I am scanning a magazine article using my HP all-in-one 5610. Scanning into Ubuntu 9.04 using XSane. XSane is taking the entire scanner bed as the image, so that there is a lot of empty space around the magazine page in the scanned image, and the magazine page is quite small. If I then print the image, the magazine page only fills the upper left corner of the page. And the writing is very small.

I want the scanned image to be such that I can email it to someone, and when they print it, the magazine page I scanned will fill a standard 8 1/2 x 11 page. What is the best and easiest way to accomplish this?

---

### Post by crispy_420 on 2010-06-09
Try a virtual PDF printer. Think there is one called cups-pdf in repos. Also doesn't xsane allow for cropping or am I wrong?

---

### Post by swarup on 2010-06-09
> **crispy_420 said:**
> Try a virtual PDF printer. Think there is one called cups-pdf in repos. Also doesn't xsane allow for cropping or am I wrong?

If xsane allows for cropping, someone will need to give me a tip as to how to do it. I haven't seen any such option, for cropping.

As for cups-pdf, is that something I would use to edit the image after it is scanned?

---

### Post by crispy_420 on 2010-06-09
Cups-pdf will allow you to send the final document to the other person in just the format you would like them to get it, so an 8x11 sheet in your case.

As a work around until a better option is presented could you scan as an image and import into GIMP to do the adjustments (size, borders, etc.) and print to PDF from there? 

I will have to look into sane more as far as cropping.

---

### Post by swarup on 2010-06-09
I was playing with GIMP prior to starting this thread, and hadn't yet figured out how to crop. But I'm sure it must be straightforward.

I just found on another forum, someone has written the following regarding cropping in xsane:
> 
The Preview mode is not enabled by default, and you need the Preview mode to be able to auto crop.

When I open xsane, the preview mode does not start up. If anyone knows how to enable it, please let me know.

---

### Post by swarup on 2010-06-09
I found out how to do it. One just has to go in xsane to Window -> Show Preview. Then check the box, so "Show Preview" is enabled. There one can opt to see a preview of the scanned image. Click on the "acquire preview" to have the scanner make a preview for you. Once the preview of your scan shows up in the preview window, you can crop it however you like. When you give the order to make the scan, the image will then be scanned exactly according to the cropping you set in the preview window.

---

### Post by ajgreeny on 2010-06-09
When you open xsane make sure you have "Viewer" chosen in the top right hand box and then you can chose "Acquire preview" and then crop the preview before you actually do the final scan.

---

### Post by crispy_420 on 2010-06-09
Problem solved right?

Scan

Crop

Print to PDF

Email

---

