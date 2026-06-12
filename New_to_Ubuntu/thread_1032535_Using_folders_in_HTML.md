---
title: "Using folders in HTML"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by dmalloch on 2009-01-06
I am having difficulty using Firefox to display an HTML page in Ubuntu. A simple version of the code is:

<html>
<head></head>
<body>
<img SRC="illustrations/Mushroom.jpg">
</body>
</html>

Under Vista, Firefox displays a picture of a mushroom contained in the folder "illustrations". Under Ubuntu no picture is displayed until I include "mushroom.jpg" in the same folder as the html code and then change the code by removing reference to the folder "illustrations". Is this a Linux issue?

---

### Post by MusicMastaMike on 2009-01-06
Your code should work the same on both platforms.  However, in Linux, all filenames and folder names are case sensitive, so Illustrations is different from illustrations.  Maybe that's your issue?

---

### Post by The Cog on 2009-01-06
Could this be a question of case sensitivity? You call it mushroom.jpg in one place and Mushroom.jpg in another. Remember that Linux (and UNIX) are case sensitive.

---

### Post by dmalloch on 2009-01-06
Hello MusicMastaMike and The Cog..

Your diagnosis and advice were dead accurate.  I had written all that HTML code in Windows where I was not overly concerned with case-consistency.  However, mea culpa, all the HTML manuals and tutorials tell you to watch out for this.  Lesson learned!

---

