---
title: "CVS questions"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by flylehe on 2009-03-25
Hi,
I just started using CVS. My questions are:

1. Do we need a CVSROOT on my local working space computer and another CVSROOT on my repository server all the time? When creating a cvs repository in the server, I remember we have to specifiy CVSROOT and then cvs init, but after that it seems to me the server doesn't require CVSROOT anymore.

2. When adding a new directory from local to the repository, here is what I do now: manaually mkdir a directory with same name in repository, checkout it to my local to cover the same name local directory and cvs add it to repository. I was wondering if there is another way to add a directory without any operation on the repository server side?

Thanks!

---

### Post by Anthon on 2009-03-25
CVSROOT is two things. 
1) A directory underneath the top of the repository on the server, you can check it out and make changes and commit, and that will influence the (future) behaviour of the server *NOT* of the client. 
So if your repository is /srv/cvsrep there should be a directory 
/srv/cvsrep/CVSROOT. The directory is created when you init the repository by e.g. doing 
  cvs -d :local:/srv/cvsrep init 
on the server.
2) CVSROOT is also used to call what is used on the client to access the repostory on the server. e.g. ':pserver:myname@servername:/src/cvsrep'. That CVSROOT is only for the client (even when used on the server it only is used as a client cvs).
---
If you have checked out the toplevel directory of the repository with something like:
   mkdir localrep
   cd localrep
   cvs -d :pserver:myname@servername:/src/cvsrep login
   cvs -d :pserver:myname@servername:/src/cvsrep checkout -l .
you can now create a directory on the server with
   mkdir newsubdir
   cvs add newsubdir
(don't take my word for, check that it is there ;-) )

---

### Post by flylehe on 2009-03-25
Thank you!

1. In you answer to my second question, I am not quite sure about how you add the new directory to the server. 

In my case I am connecting the server via ssh, so I have my CVSROOT stored in my .bashrc. If I have a new local directory called "localrep" that does not exist in the repository then I enter it and I do this
```

cvs checkout -l

```
I would get error:
> 
cvs [checkout aborted]: must specify at least one module or directory


Besides, do you also mkdir in repository a directory with the same name as the new local one?

2. another question is if I would like to have copies of multiple local directories in repository, must they be under the single common toplevel repository directory. Can I create multiple repositories to hole the copies of different local directories? If no, is it because we can only specify one single path in our local CVSROOT variable?

Thanks a lot!

---

### Post by Anthon on 2009-03-25
You really need to specify a dot '.' after the -l subcommand to checkout:
  cvs checkout -l .

---

### Post by flylehe on 2009-03-25
Thanks!
I find that with "cvs add local_directory" will only add the "local_directory" and not its subdirectory and files to the repository. Does that mean we have to add for each subdirectories and files? 
Thanks!

---

### Post by Anthon on 2009-03-25
That behaviour is correct. Some Windows clients that I know can add recursively (but that is implemented as multiple calls.
To add directory abc and the directories under abc recursively use:
  find abc -type d -print0 | xargs -0 -l1 cvs add
To do the same for files requires that the CVSROOT/cvswrappers file is up to date (and checked in!) with information for extensions that indicate binary files:
*.gif -k 'b'
*.jpg -k 'b'
*.jpeg -k 'b'
etc

If that is not in place the files get checked in as ascii, and will:
a) checkout incorrectly on Windows systems ( where \n is expanded to \r\n
b) checkout incorrectly if expandable string like $Id$ happen to be in the binary.

If you only have a few files that are binaries and you don't want (or cannot generically add the extension to cvswrappers. You have to add those binaries first with:
  cvs add -kb filename1 dir1/filename2
or something like:
  find  abc -type f -name "*.bin*" -print0 | xargs -0 cvs add -kb
after which you can do 
  find  abc -type f -print0 | xargs -0 cvs add
for the rest of the files (you would also use the latter if all the binary extensions are properly added to cvswrapers).
Don't forget to commit with
  cvs commit -m "your commment" abc

---

### Post by flylehe on 2009-03-25
Thanks Anthon!
So the binary files and ASCII files should be checked in differently and all the files by default will be checked in as ascii.
 
Does the same thing happen to checkout?

In your examples, image files ought to be treated as binary. Can I get the info for a arbitrary file type from somewhere?

---

### Post by Anthon on 2009-03-25
Once the server side knows which files are binary and which are ascii. It will store that information on a file by file basis (so it doesn't help to change the cvswrappers file after the fact, you would have to change any wrong files with cvs admin ...)
After a file has been checked in correctly you don't have to do anything anymore.

You can go for safe, and check everything in as binary. But CVS doesn't allow you to do a diff on binary files, so that is not really an option in most cases.

Most files should go in as binary, inclusing UTF-8 XML files. Most source code (unless you use special utf-8 in your source code) should go in as ascii. 
For those files the diff (which is only possible on ascii) is actually useful.
So better a few extensions too many added to cvswrappers than a few too little.

The 'file' command might help with finding out about the different files you have.

---

