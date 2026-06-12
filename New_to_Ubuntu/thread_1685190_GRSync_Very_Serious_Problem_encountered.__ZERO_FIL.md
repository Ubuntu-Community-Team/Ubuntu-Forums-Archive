---
title: "GRSync Very Serious Problem encountered.  ZERO FILES COPIED!"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by Kellemora on 2011-02-10
Hi Gang

I've been using GRSync for quite some time now without a single problem.  ZERO Errors.  All files perfectly intact.  UNTIL NOW THAT IS!

Backups have all their folders but NO FILES, they are ALL MISSING.  ALL FOLDERS ARE EMPTY!!!!!  GRSync is producing THOUSANDS of pages of errors.

ALL of the Setting were Identical to the previously Working settings.
I did change one setting After I Discovered ZERO FILES at Destination, reran GRSync and found the same problem still exists, NO FILES at Destination, only the Empty Folders are copied over there.

Here are my settings (that have worked for years now)!
All BASIC settings are selected in the top section.
In the bottom section:  Delete on Destination, Verbose, Show Transfer Progress & I've tried with and without Windows Compatibility.

The above settings WORK perfectly to copy files from a computer to an external hard drive on the same computer, or on a remote computer in a different building.  Also, the main external hard drive is mirrored to an offsite external hard drive using GRSync with the above settings with ZERO ERRORS.

We have a 2 terrabyte NAS device on the LAN now!
I used GRSync with the above settings to copy the external hard drive over to it.  Discovered all Folders were there, but ZERO FILES....
Tried it a second time with Windows Compatibility turned off.  Found all Folders but still ZERO FILES.....

The Log File shows the following error roughly 150 thousand times:
rsync:  mkstemp "/home/gary/.gvfs/familylibrary on storaMirrorTwoOfFileServer/BUSINESS/Permanent/AccountingData/(filenameshere)" failed: Operation not supported (95)

The first time I ran GRSync with Windows Compatibility turned on (it's usual setting) All of the Files received the error:
rsync:  failed to set times on "/blah/blah/blah/" Operation Not Supported (95).

My ONLY clue that may be helpful here is:
We have 8 computers that are mirrored to their respective folders on an external hard drive (named File Server) on a computer dedicated to that service.
If I recall, we could NOT "PUT" files onto the external hard drive from the source computer.  So, to solve this problem, GRSync running on the computer WITH the external hard drive "FETCHES" the data from each of the other computers and stores it on the external drive connected to itself.

An off-site computer with another external hard drive (named Mirror of File Server), "FETCHES" the data from the on-site external hard drive and stores it.  Zero Errors doing it this way.

So obviously my original GRSync problem was never solved!
GRSync can only Fetch and store files, it cannot PUT files anywhere else!
This makes my 2 terrabyte NAS totally useless to me!  Because since it is not able to run GRSync itself it cannot FETCH files to store on itself.

We had a similar problem back when I was leasing on-line storage space!
We could not PUT our files there using GRSync, but using a Windows backup program to simply Copy all Files and Folders we could do it with zero problems.

There has to be a WAY to SAVE all Files and Folders to a remote destination drive available in Linux.  And YES those locations were MOUNTED first, else it wouldn't work at all, naturally!

Any Ideas on how to get GRSync (or some other more reliable program) to "PUT" files onto a remote Hard Drive or NAS?????

The NAS cannot "FETCH" files in order to use GRSync or RSync for this purpose!

I can manually COPY files to the NAS without a single problem or error!
Seems to me the most touted program should be able to do likewise!!!!!

TTUL
Gary

---

### Post by Zill on 2011-02-10
Kellemora:
> **Kellemora said:**
> You're absolutely right there LovingLinux!

[COLOR="Red"]I am moving on[/COLOR], from FireFox to Chrome [COLOR="Red"]and from Ubuntu to Debian!
[/COLOR]
TaTa
Are you now running Ubuntu or Debian?

---

### Post by Kellemora on 2011-02-10
Hi Zill

Still using Ubuntu 8.04 on most of my computers....

Running 10.04.1 on my daily computer, but have not yet moved all of my serious work over to it yet.
Been trying various Linux program on it to see if I could find some to take the place of those I've been running in Wine.....

But since we cannot get 10.04.1 to run on the majority of our computers, I can't move over to it.....

But on the RSync problem.
Seems like I've had this problem from day one, and since I've been using the work-around for it for so long.  I had almost forgot that I never was able to get RSync to PUT a file somewhere.  I always had to go to the Destination and FETCH the file from it's source....

NO ONE has come up with a Solution for this problem in like what 3 years now?  

I did have my ISP give me the Terminal Codes he uses for copying MASSIVE files to an off-site backup, but then later when I told him it didn't work, he then admitted that he too was running it on the off-site computer and Fetching the files.

Apparently RSyng or it's graphical counterpart GRSync does not have the capability to simply COPY files from point A to point B!

Guess I'll have to STILL keep a Windows Computer to handle the SERIOUS things that need to be handled!  Having backups is a very serious issue!

TTUL
Gary

---

### Post by b0b138 on 2011-02-10
rsync is capable of putting files somewhere, it just has to use an ssh connection (at least thats what I read, haven't done it myself)

Another way would be to mount the remote location in fstab, either samba or nfs, on each of the 8 computers. Say you mount at /mnt/backup. The rsync command would be something like rsync --options /path/to/source /mnt/backup.  This way, the over the network stuff is handled by something other than rsync

---

### Post by asmoore82 on 2011-02-10
You need a storage solution that supports rsync over SSH transport natively.

A lot of NAS boxes do and the ones that don't can be hacked to do so
since they all run on Linux anyway.

The monster efficiency of rsync comes from having the rsync agent
code running on *both* sides of the transfer.

But back on topic &#8230;
For starters, You need to tell rsync to categorically ignore all ~/.gvfs folders.

&#8230; so what network transport are you actually using?

Please don't say Samba/CIFS.

---

### Post by Kellemora on 2011-03-02
If I turn OFF all OPTIONS it will copy the folders and files in them each and every time, however it takes THREE DAYS to do this EACH TIME I run RSync.

Since RSync seems to always work perfectly when FETCHING Files, I'm taking the REVERSE ROUTE and instead of trying to use RSync to Load the NAS, I'm manually copying the files to the NAS and then will use RSync to Fetch the Files from the NAS to the External Hard Drives as redundant mirrors of the NAS data.......

What I had before the NAS was quite simple.  A computer dedicated to holding all the files.... RSync was used to mirror ALL these files, retaining, times, permissions, etc. to an External Drive...  This External Drive then became our Main File Server.  Files are fetched from it, edited and placed back onto it.  The dedicated computer would read the external HD and copy it to it's internal HD as our mirrored backup.
Then an offsite computer would run RSync and FETCH (copy) the data from the File Server External Hard Drive to it's External HD as an Off-site mirror.  We could NOT use RSync from the dedicated computer to PUT the files onto the external hard drive of the remote computer.  Something I had forgotten about since once everything is working right, I don't mess with it....

But, trying to place the files onto the NAS brought back the memory of those NIGHTMARES of trying to use RSync........
And NOW that I know the NAS is slower than the 7 year itch......
Well, I'm just considering it a BAD BUY and will use it for local files that don't get changed or something where I don't need it for anything important....  I assume USB2.0 must be exponentially FASTER than a 1gig LAN!!!!

As an aside:  I experimented a little with a WinDOZE computer, it placed files, copied files, TO the NAS with ZERO PROBLEMS...... Retaining all the permissions, times, etc....

TTUL
Gary

---

