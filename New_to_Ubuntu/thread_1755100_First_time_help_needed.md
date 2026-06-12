---
title: "First time help needed"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by ngreen on 2011-05-10
hello all.  I have a .daa file that i need poweriso to extract it.  I have read some tutorials on this but i just cant get it.  I need help right from installing poweriso through extracting the .daa file.  I have been using linux for 2 days.  Please help lol!  Thanks!

---

### Post by TheNerdAL on 2011-05-10
This link might be of use: [http://maketecheasier.com/how-to-extract-daa-files-in-ubuntu/2008/06/19](http://maketecheasier.com/how-to-extract-daa-files-in-ubuntu/2008/06/19) 

If you're confused about what that webpage is saying and don't know what to do, then feel free to post.

---

### Post by ngreen on 2011-05-10
ok well here is my problem......i type in what the tutorial says but it doesnt do anything.  i have the tar file saved in downloads.  im afraid i dont know the correct path.  like windows would be c,desktop, downloads.........i really want to learn linux but am struggling.  actually the .daa file i have is a group of linux books!  lol thanks

---

### Post by silex89 on 2011-05-10
Hi!. Look, there's a really good application to manage PowerISO images in ubuntu. Is called AcetoneISO, is very easy to use (all the options are graphical).

You can install it from synaptic or typing in the terminal

```
sudo apt-get install acetoneiso
```Then you put your password... And that's all! :D


Good luck!


Regards

---

### Post by trellis2 on 2011-05-13
[http://www.poweriso.com/poweriso-1.2.tar.gz]("http://www.poweriso.com/poweriso-1.2.tar.gz")
Ill try to give this step by step. You can cut copy and paste the commands, but you'll learn more if you type them and try to understand them
1. Download poweriso-1.2.tar.gz from here [http://www.poweriso.com/poweriso-1.2.tar.gz]("http://www.poweriso.com/poweriso-1.2.tar.gz")

2. Go to the directory where you will install poweriso for linux. 
Me@MyComputer:$ cd /usr/bin

3. Extract and install in this one step. Get the path to the downloaded file correct. I type "sudo tar -xf " the drag the folder into the terminal window so that the path to the file shows up. NOTE: the long names are enclosed in quotation marks '/home/longname/powriso.tar.gz'. 
Me@MyComputer:/usr/bins$ sudo tar -xf '/home/Me/Downloads/poweriso-1.2.tar.gz'

4. Change directory to where the file was downloaded.
Me@MyComputer:/usr/bins$ cd ~/Downloads

5. Look at the help file " Betta feed your brain fool!" Me@MyComputer:~/Downloads$ sudo poweriso -?

6. Here you will have to insure that the paths are correct, but this is the basic form the command will take. 
Me@MyComputer:~/Downloads$ sudo poweriso convert /home/Downloads/MY.daa -o /home/Downloads/MY.iso -ot iso

You should be able to take it on your own from here. Let the forum know if this works for you.

---

### Post by trellis2 on 2011-05-13
The above commands convert .daa to .iso. To extract use something like this:

extract <image file> <dir/file name>   Extract files/directories from image file.
     Example:  Extract all files and directories in root direcory of /home/sam/test.iso
               to /home/sam/test recursively.
     Command:  poweriso extract /home/sam/test.iso / -od /home/sam/test

FYI: guys the question was about .daa files, did anybody actually try the advice they were giving on dealing with .daa files.

---

