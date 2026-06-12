---
title: "Quary for developers"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by chandrav23 on 2010-06-05
Dear Guys,
I am new and biggner for ubuntu(liunux)
 
I would like to notice about something for developers.
 
When we are using CAT command(to create;to append or to crate multiple files)
 
cat><filename>--------to create a new file
cat>><filename>-------to append 
cat><file1> > <file2>-----to create multiple files....
 
example:If someone are  trying to append something to existing file but unfortunately they entered only one graterthan symbol(>) insted of (>>) it suppost give some error info like(file name existed)
 
But in ubuntu no error msg eventhough its going to create new file and we are going to loose existing data.
 
 
Pls respone to this quary and try rectify in the future
 
Regards
Chandra

---

### Post by BoneKracker on 2010-06-05
No, you're not going to get an error, because 'cat > existing_file' is ok.  That is how you would intentionally over-write a file.

Also, this issue has nothing to do with 'cat'.  This is an issue of io redirection, which can be applied to any command that utilizes stdin, stdout, or stderr (which is just about all of them).

[http://www.linuxsa.org.au/tips/io-redirection.html](http://www.linuxsa.org.au/tips/io-redirection.html)

[http://tldp.org/LDP/abs/html/ioredirintro.html](http://tldp.org/LDP/abs/html/ioredirintro.html)

[http://www.faqs.org/docs/abs/HTML/io-redirection.html](http://www.faqs.org/docs/abs/HTML/io-redirection.html)

---

