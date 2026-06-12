---
title: "trying to convert eml files to mbox"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by stinger30au on 2009-08-13
g'day

im trying to convert a few hundred emails that were saved from outlook express
the files are listed as

my data.eml

im trying to convert these for use in evolution

after much reading i found this post

[http://ubuntuforums.org/showthread.php?t=45838](http://ubuntuforums.org/showthread.php?t=45838)

in particular this one near the bottom


------------
 				 				**Re: how to open a forwarded email (.eml format)** 			
 			 			 		   		 		 		Here is a way to do it using Thunderbird. I know it isn't pretty but it works. The method involves converting it to mbox format and then moving it into T-bird in a special inbox of your choice.

1)  apt-get install ruby
2)  from the URL:  [www.broobles.com/eml2mbox]("http://www.broobles.com/eml2mbox")  download and unzip eml2mbox.zip into your home account
3)  create a receiver directory in your account, call it my_emls or something
4)  move one or more of your saved  *.eml's into this directory
5)  in T-bird create a folder under Local Folders, call it Inboxmbox
6)  run the following command in your account:
        ruby eml2mbox.rb ./my_emls /home/<your account>/.mozilla-thunderbird/xxxxxxx.default/
             Mail/"Local Folders"/Inboxmbox

       (you will have to find the value of xxxxxxx by looking under .mozilla-thunderbird)

Notes:  for some reason you must fully qualify the last argument or it can't find the file.
              you must completely clean out the my_emls folder each time or ALL the entries will be      put in again.
              you will be given the choice to (o)verwrite, (a)ppend or (c)ancel on the Inboxmbox folder.

I am working on a script to perform the conversion and move as the command is so darn long to type in each time.
For some reason I am getting more and more of these .eml attachments than ever before. If anyone else has noticed this please let me know.

------------------


does anyone know how to make this script take multiple .eml files and convert to mbox format

i have tried to copy the .eml files in to their own directory and the this command

 ruby ./eml2mbox.rb ./*eml /media/data2/eml.convert


and i get this output

Specified dir : ./1963.eml
Specified file: ./3 more fotos, London.eml

[./1963.eml] is not a directory (might not exist). Please specify a valid dir


looks like it is trying to create an extra directory

what i want this to do is read each of the files in the directory the .eml files are save them in mbox format to the same directory in .mbox format

i reckon my command line is correct. any ideas?
thanks

---

### Post by stinger30au on 2009-08-14
its cool, after more reading and putting a few bits together heres how its done

first install thunderbird from repos

next install the eml converter from here

[http://nic-nac-project.de/~kaosmos/mboximport-en.html](http://nic-nac-project.de/~kaosmos/mboximport-en.html)

next install it to thunderbird like this

[B]To install the extension, follow this procedure:
[/B] - download the xpi file that you find in this page or in the homepage, right clicking on the link and choosing "Save target as";
- in Thunderbird, go in "Tools" --> "Addons" (or "Extensions") and click on "Install";
- pick the xpi file you downloaded and follow the instructions;
- restart Thunderbird. 

then in thunderbird tell it to import all the eml files from what ever directory u want

then in thuderbirs click the tools, import.export tools and hit export folder

let it save the folder to a directory

next

fireup evolution

creat a new directory under the inbox and then go and click on file import and point it to the file you just created from the export tools

it will read it and ask you where to install the files

point it to your newly created directory in the inbox in evolution and it will import the lot including attachments to evolution

do this for all files/directorys of eml files you have

after this is done make sure to back up evolution

---

### Post by HermanAB on 2009-08-14
Howdy,

In my experience the easiest way to convert email is via an IMAP mail server.  You can install the Citadel mail server in about 20 minutes using the Citadel Easy install Script.  Then use Outlook or whatever on Windows, make a new account on Citadel and click drag drop all the email to the server.  Then repeat with Thunderbird or whatever on Linux in the reverse direction - make a new account to the Citadel server and click drag drop.  This way you use the native software to read/write its own local file format so the conversion is perfect.

---

### Post by stinger30au on 2009-08-14
my post #2 works perfect as well, comes in handy for folks like me who have no imap server handy.

works well & the import tool will scan sub directorys as well
piece of cake


what ever works i guess

---

### Post by happyhessian on 2010-01-10
For the more casual user, check out this great post.  It's kind of comical but it works:

[http://www.zyxware.com/articles/626/how-to-open-eml-files-and-included-attachments-in-ubuntu-or-any-other-gnu-linux-distro](http://www.zyxware.com/articles/626/how-to-open-eml-files-and-included-attachments-in-ubuntu-or-any-other-gnu-linux-distro)

---

### Post by stinger30au on 2010-01-13
> **happyhessian said:**
> For the more casual user, check out this great post.  It's kind of comical but it works:

[http://www.zyxware.com/articles/626/how-to-open-eml-files-and-included-attachments-in-ubuntu-or-any-other-gnu-linux-distro](http://www.zyxware.com/articles/626/how-to-open-eml-files-and-included-attachments-in-ubuntu-or-any-other-gnu-linux-distro)


copy/pasted here to be preserved for prosperity sake
------------------------------------------------------------------------------------------
     If you are a regular GNU Linux user there is a very good chance that you will come across emails forwarded to you as .eml files once in a while. .eml is the extension used for files saved as emails from Microsoft outlook or outlook Express. It is normally just a matter of opening these files with gedit as the files are plain text files unless they have attachments. If the attached .eml files themselves have attachments you run into the problem of actually having to open these base64 encoded attachments. The default set of applications in Ubuntu does not directly allow you to do this but there is an easy work around for this problem.

  
[LIST=1]
[*]Open evolution and compose a new mail.
[*]Attach the .eml file as an attachment to this mail.
[*]Save the mail and close the compose window.
[*]Select the mail from the Evolution main window.
[*]Below the viewing pane there will be an option to view the attachment inline. Click on it and enjoy.
[/LIST]
 This is only a workaround for the problem but it is an easy work around. If you know an easier solution please do share it with us for the benefit of everybody out there.

---

### Post by nsznaj on 2011-09-20
dear all

I have an eml file, I just want to open it though gmail doesn't make it... I just see numbers and letters without any sense..

I wouldn't install too many things nor want to use the ubuntu mail viewer just for this time...

Is there any way to view this .eml file without doing too much trouble?

Cheers,
Nahuel,

---

### Post by Polydorus on 2012-12-22
The post above yours says:  "It is normally just a matter of opening these files with gedit as the files are plain text files unless they have attachments."

Have you tried that?

---

### Post by overdrank on 2012-12-22
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

