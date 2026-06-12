---
title: "error while using ftp using bluefish"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by iamfletch on 2008-06-20
I am attempting to connect to a ftp server using the bluefish.

I connected to my ftp fine using firefox, just typing in:
ftp://iamfletch@as-sos.com
it prompted me for my password and it was fine.

When looking at the video on the bluefish website, [http://bluefish.openoffice.nl/movies/working_with_remote_files.html]("http://bluefish.openoffice.nl/movies/working_with_remote_files.html"), i did the same but with no luck!
i typed in:
ftp://iamfletch@as-sos.com
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=74759&stc=1&d=1213977283[/IMG]

I dont know what to do. any advice?

---

### Post by Perow on 2008-06-27
I'm stuck with the same problem, except that I typed in "sftp://", as mentioned in the movie.

---

### Post by iamfletch on 2008-06-27
Try connecting using nautilus (file browser) or Places->Connect To Sever... You will get a similar error. I have done alot of reading on this, and it is probably your hosts fault. I have been told that is because the reply name of the FTP server is too long. Apparently this problem has been fixed in an update, i am still getting an error tho.

I am using fileZilla while looking for a solution, is there any plugins or anything for bluefish that have ftp? Or a new editor with ftp built in?

Also can i mount a ftp directory or similar using different methods?

---

### Post by GaryH on 2008-07-06
I have the same ftp problem with bluefish. Nautilus and xterm connect to my ftp server just fine. Installing the gnome virtual file system with synaptic didn't help. BTW - bluefish flat doesn't work on my macbook.

---

