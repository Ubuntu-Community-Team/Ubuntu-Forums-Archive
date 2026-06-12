---
title: "TAR - How to Extract ONLY a specific Directory"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by mistypotato on 2009-12-21
Hello,

After 2 days of carefully Googleing and studying every resource I could find, I still have not been able to accomplish the restoration of a specifc directory To a specific location using TAR.

I can restore (extract) the directory WITH it's parent...but not JUST the desired directory.

Here is my example....

I have a TAR file mytar.tar

Within that tar file I have backed up /var/www from my server.

I want to EXTRACT / RESTORE ONLY the WWW directory WITHOUT overwriting the /VAR directory but there appears to be no way to extract /WWW without also extracting /VAR

Of course, I could just do the extraction and then COPY the www directory but that seems to defeat the purpose or convenience.

the command I use is....

Tar -xvpf mytar.tar var/www

What is the correct command to ONLY extract the /WWW directory so that it overwrites the existing WWW directory but NOT the /VAR directory?

Thanks

---

### Post by t0p on 2009-12-21
Does it have to be a command line solution?  I can never remember all the options and switches that come with tar.  Sorry!

You can do it through the Ubuntu "Archive Manager" (is that fileroller?)  Right-click the archive, select "Open with Archive Manager"; highlight the directory in question and do an "Extract to...".

The only other suggestion I have is:

```
man tar
```

Sorryyy!!  :)

---

### Post by atomizer on 2009-12-21
[This post]("http://www.unix.com/unix-advanced-expert-users/12825-extract-sub-directory-form-tar-file.html") shows your on the right track.

Is it not a typo? (**/**var/www instead of var/www)

---

### Post by mistypotato on 2009-12-21
thanks for the reply :-)

If I use a leading slash, it wont work.
Actually, it wont restore JUST a subdirectory with OR without a leading slash.

When I try to use the syntax listed at Unix.com as the correct way to extract a subdirectory, it ultimately comes back with the error..
[B]
www not found in archive[/B]....even though I confirm it's there with the -t command

I am FORCED to include the complete path...at which point TAR will adamantly restore the COMPLETE path, (including all files in both the directory I want AND the parent directory) but never JUST the directory I want restored.

When I created the Tarball, I Tarred /var/www

Now I want to extract ONLY the www files in the www directory, TO the www directory on a different server, WITHOUT overwriting the existing /VAR directory.

---

