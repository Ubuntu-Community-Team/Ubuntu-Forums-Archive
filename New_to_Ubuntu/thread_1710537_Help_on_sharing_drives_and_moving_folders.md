---
title: "Help on sharing drives and moving folders"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by n4pgw on 2011-03-20
*This is a home network only, not commercial.*  
(more details under the base request)

I think I figured this out with Windows/samba, but not in Linux/NFS.  I successfully shared children's movies without having to log into the server or have an account.  But, from Linux, the visitor can go all the way to root.  I need to cap off anything below /movies/adult/youth/children (or whatever level appropriate for the computer.  )

I also want to auto-login when my wife or I boot our computers giving us access to all movie levels and to another folder (for files we store, share and backup to the server) without having to enter a password each time.  I do want this folder protected from guest access.  

I have a folder /home which is a RAID mount, under which I have /home/movies.  I am moving movies to a separate drive and need to move the folder.  I also wonder if I can put /srv (currently empty) on the same drive as /home but not under /home/srv. (still acceptable to me) Or, should I have /srv/home?

When a visitor brings in a laptop, I want them to have a separate password for movie access to the adult level.  Free access to childrens and youth is fine.

Thank you,
Buck

Read the details below:




My server is configured as follows: 

IDE-1
[COLOR=DarkRed]80GB Raid1-1A[/COLOR]
***[COLOR=DarkSlateGray]40GB Raid1-2A[/COLOR]***
IDE-2                / [COLOR=DarkRed]1[/COLOR] 
[COLOR=DarkRed]80GB Raid1-1B[/COLOR]
***[COLOR=DarkSlateGray]40GB Raid1-2B[/COLOR]*** 

Ubuntu server was installed using all the space on Raid1-2 except for /home which was created on Raid1-1

In the /home folder, I created /movies where I upload all our movies to be viewed at any computer.  I also created individual accounts, (which I may delete,) for myself, my wife and our young child.  Today, I copied the movies to a 500GB USB drive and attached it to the server.  It is not part of the raid or an extension to an internal drive, just a separate drive.

I learned today, that the tradition is to use /srv for shared files.  It is empty, but I believe that is where /movies belongs.

My primary goal is to have two shared (base) folders: **movies** and **files**.  

**Movies **are to be stored on the 500 GB USB drive.  There are three categories of movies: Children (pre- and early school age), Youth (older and teens), Adults (everyone else). I am configuring a guest computer in a similar way with three guest logins.  

I want my child's computer and the child-guest login to only access the childrens movies.  I want the youth-guests to have access to childrens and youth movies.  I want the adult-guests and my wife and my computers to have full access to all movies. 

**Files **folder is to be restricted to only my wife and my computers/laptops/ipods for storing and sharing files.

Today, I setup samba and have open read-only access to all movies from any of the computers.  The windows machines all have a shortcut folder on the desktop for easy access. 

**What I want:** 

[LIST]
[*]My wife's and my computers to automatically log into the server and link to the files and movies folders.  (two different drive letters in Windows.)
[*]My child's computer to link to the children's movies folder only.
[*]My three guest accounts to log into the appropriate movies folders.
[*]Guest's computers to see children's and youth movies w/o password, or adult with.
[/LIST]
[B]
What I am thinking:[/B] 
I can stack the movies folders and set samba shares for the ms computers to link only to the appropriate base folder:
/movies/adult/youth/children 
(children see only children movies, youth see youth + childrens...)

The files folder would only be accessed by my wife's and my computers so we can share, store and backup files. 

**Complications:** My and my child's computers will be linux, but my wife's and the guest computers will be windows.  So, they use Samba, and we use NFS.  
Visitors who bring their own computers should only have access to movies. I am thinking a password to the adult level will be sufficient. 

(BTW, the movies are categorized by interest levels, not levels of decency.)

---

### Post by outleradam on 2011-03-20
Is that a question?  Since you seem to already have it planned out..  I'll just say way to go!

---

### Post by n4pgw on 2011-03-20
> **outleradam said:**
> Is that a question?  Since you seem to already have it planned out..  I'll just say way to go!

LOL, that's what happens when I try to forum after midnight.

Thank you for the compliment.

I do have it planned.  But I don't know how to implement some of these things.  I thought I had windows guests access to the children's movies, but this morning the links don't work. ... back to samba...

I'll try this a few questions at the time. 
I will stack the movies so they are /movies/adult/youth/children. 

1a) When my child logs into her **ubuntu** computer, how do I get it to automatically log into the server and have read-only access only to the children's movies.  (I want to have a link on her desktop). 

1b) When my child logs into her **windows** computer, same question as 1a...

2) When my wife logs into her **windows** desktop, I want her to automatically log into the server and have access to all movies and to the family /home folder (which we will share).  How do I set this up?

3) When I log into my **Ubuntu** desktop, I want the same thing as my wife has.  How? 

4) When visitors bring their own laptops and they log into the network, I want them to have open access to the youth + childrens movies, and password access to adults movies.  How?

That's all for now.  I am going to rearrange the movies on the new drive and see if I can fix the samba accesses.

Thank you
Buck

PS Everything I am asking, I have tried to find through searches.  That is how I got this far.  I find lots of invalid information that goes as far back as Ubuntu 5.  I even had to reinstall the server twice due to following older version advice, or just bad advice.  I am hoping to avoid doing that again. Thank you.

---

### Post by n4pgw on 2011-03-21
I have varied my plans just a little, but I decided that instead of keeping this open, I will open new threads for each problem I am having.

Thanks

---

