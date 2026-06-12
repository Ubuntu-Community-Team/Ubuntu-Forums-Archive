---
title: "search tools like &quot;tracker&quot;"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by julianb on 2011-05-16
tracker is supposed to allow instant indexing of files and file contents. So, for example, I'd be able to search for "julian" and find all of the files that have my name in them. Even if a file was created in the last minute or so.

This is also how Recoll is supposed to work, and it's how OSX's search tool DOES work.

Problem being, on my system tracker starts up but doesn't ever find files; Recoll doesn't start and produces the output, "Segmentation fault" if run from terminal.

Do you use one of these tools, or something providing the same capabilities? If so, what version of Ubuntu / what desktop environment are you using where they work?

---

### Post by jtarin on 2011-05-16
I use the old standby "locate", which is based on "slocate".
Type "sudo updatedb" in a terminal give it a few moments to run the first time then when you want to search for something use the command "locate <filename>". Use the parameters "more" or "less" depending on your results to allow you to scroll back and forth through screens.You will need to update the database manually to include any new files that have been added since the last update. You can also make a cron job to do this automatically.

---

### Post by julianb on 2011-05-16
I'm familiar with locate, but the part about indexing right away (as promised by tracker/recoll/mac osx) is what I was looking for.

no luck so far :(

---

