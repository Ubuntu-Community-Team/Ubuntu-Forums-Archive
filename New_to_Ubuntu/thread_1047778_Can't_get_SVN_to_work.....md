---
title: "Can't get SVN to work...."
date: 2009-01-22
forum: New to Ubuntu
---

### Post by sum janus on 2009-01-22
Hi guys,

Sorry if this is the wrong place to post, I still consider myself a beginner :) .

I'm having difficulties getting Subversion to work.  I have a PHP project I am working with two other developers on.  Through my web host's panel, I created the repository, and entered in a URL and some usernames / passwords.

The problem is that I can't figure out how to get into the repo from my computer, through the command line using the svn command or by using RapidSVN.

I understand how SVN works (kinda), but have absolutely no idea how to work it.  For example, how do I connect to the repository?  If I have a set of files I want to make serve as the starting block, how do I push those in?

I'd appreciate help, either using the CLI or RapidSVN (or another GUI client, I'm not picky!), but I like using the command line because I find you get more flexibility that way :) .

Thanks so much!!
Eric

---

### Post by sp0nge on 2009-01-22
From the MAN page...

```
       Subversion  is  a  version control system, which allows you to keep old
       versions of files and directories (usually source code), keep a log  of
       who, when, and why changes occurred, etc., like CVS, RCS or SCCS.  Sub&#8208;
       version keeps a single copy of the master sources.  This copy is called
       the  source  ‘‘repository’’;  it contains all the information to permit
       extracting previous versions of those files at any time.

       For more information about the Subversion project, visit http://subver&#8208;
       sion.tigris.org.
```

SVN is pretty straight forward. The syntax is simply:
```
svn <command>
```

The help command will list all available commands that you can use:
```
svn help
```

I hope this helps a little.

---

### Post by lloyd_b on 2009-01-22
> **sum janus said:**
> Hi guys,

Sorry if this is the wrong place to post, I still consider myself a beginner :) .

I'm having difficulties getting Subversion to work.  I have a PHP project I am working with two other developers on.  Through my web host's panel, I created the repository, and entered in a URL and some usernames / passwords.

The problem is that I can't figure out how to get into the repo from my computer, through the command line using the svn command or by using RapidSVN.

I understand how SVN works (kinda), but have absolutely no idea how to work it.  For example, how do I connect to the repository?  If I have a set of files I want to make serve as the starting block, how do I push those in?

I'd appreciate help, either using the CLI or RapidSVN (or another GUI client, I'm not picky!), but I like using the command line because I find you get more flexibility that way :) .

Thanks so much!!
Eric

First, "check out" the empty repository (yeah, I know that sounds silly, but bear with me):
```
svn co {server} {path}
```
where {server} is the SVN repo server URL, and {path} is the path to where you want the local copy of the repo on your machine.

Next, copy the files for the starting block into that directory.

Then,
```
svn add *
```
while in that directory.  This will tell your local machine to mark all files/directories in that directory for addition to the repo.

Finally, "commit" the new files:
```
svn ci
```
will tell SVN to actually update the repo based on your local copy.

Note that you should be prompted for user/password one time (after that, this info is stored).  Each time you do a "commit" ("ci"), it should bring up an editor (probably nano, but this is configurable) so that you can add the revision comments.  Just enter your comments, save, and exit.

If you're confused about how to do something, "svn help" will give you a list of possible commands, and "svn help {command}" will give you the equivalent of a man page on that particular command.

---

### Post by sum janus on 2009-01-22
Dude!  It worked!

Thanks a lot.  I think that's what threw me off, the checking out the empty directory.
 
Something that bugged me was that I was never prompted for a password.  I *might* have gone into it before, but I'm not sure.  Is there any way I can check?

Also... when I check out a file, does that simply update me to the latest version?  So if I check out a whole directory, does that update _all_ of my files to the latest version?  Then what does update do?

And then commit... does that update whatever files I've added, as you had me do early with
```

svn add *

```
to the repository?

And last question (sorry for being so long!) is locking.  How do I lock a file, and what exactly does it do once I've locked something?

Thanks sooooo much.
Eric


Edit:
I created another test svn just to make sure that the password authentication was working.  When I tried to access it, I get this:
```

eric@Janus:~$ svn co http://test.ericvernon.com/crazy-svn /home/eric/Desktop/crazy
svn: PROPFIND request failed on '/crazy-svn'
svn: PROPFIND of '/crazy-svn': 301 Moved Permanently (http://test.ericvernon.com)

```

Wait, what?

---

### Post by lloyd_b on 2009-01-24
1.  You should NOT have been able to commit without the password, unless the repo is configured to allow unauthenticated commits.  To see if you have a password stored, look in the file(s) in ~/.subversion/auth/svn.simple - this is where the password will be stored.

2.  If you issue a "svn co" command while in a working copy directory, subversion will update the working copy from the server, for files in that directory and any subdirectories.  You can use "svn co {filename}" to only update one file, but it's better practice update entire directories at a time, to avoid inconsistencies between files.  The update will *attempt* to update all files, but may "confict" on files if changes you've made make it impossible for it to merge the changes from the server into your local copy.  I'd suggest reading [the manual]("http://svnbook.red-bean.com/") for more info on how to handle such conflicts.
     Note that while you normally "svn co" to get the *latest* revision, there are various options so that you can get ANY revision that exists in the repo ("svn help co" for more info).

3.  A commit will send to the server any new files that you've added (via "svn add"), as well as changes to any files you've changed in your local copy.

(After doing a "svn ci", it's good practice to do a "svn co" to update your local copy's administrative data for the repo (this does NOT automatically get updated when you do a commit)).

4.  Use the "svn lock {filename}" and "svn unlock {filename}" commands to lock and unlock files.  A lock prevents anyone other than you from making a commit to that file (either changing it, or deleting it) for as long as you hold the lock.

(If you do a "svn help", you'll see a list of these and other commands.)

As for your "svn: PROPFIND of '/crazy-svn': 301 Moved Permanently (http://test.ericvernon.com)" error, the 301 is an error coming from the Apache server.  I have no clue as to what's wrong...

Lloyd B.

---

