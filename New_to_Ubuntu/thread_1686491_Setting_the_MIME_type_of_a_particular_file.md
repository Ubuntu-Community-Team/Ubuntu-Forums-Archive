---
title: "Setting the MIME type of a particular file"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by le_phoceen on 2011-02-12
Hi,

this question is not Ubuntu specific, more a Gnome question. I wrote a little script with the name dummy, without extension. I would like this file to have the mime type application/x-executable or application/x-shellscript. I found some doc on the web explained how to bind a given extension with a given mime type, but here there is no extension, and I don't want to bind every file with no extension to a particular mime type. What can I do to associate a mime-type for this particular file ?

Thanks a lot :)

---

### Post by Joeb454 on 2011-02-12
Do you have ```
#!/bin/bash
``` at the top of your script?

I have several scripts that don't have a .sh extension that work fine as they are, each with that on the first line.

---

### Post by le_phoceen on 2011-02-12
Indeed ! With the addition of #!bin/bash, the file is now identified as application/x-shellscript. I suppose that when there is no extension to the file, the content is actually scan to find its mime type.

Thank you Joeb454.

PS : as a matter of curiosity, what can you put in the file to make it identified as application/x-executable ?

---

