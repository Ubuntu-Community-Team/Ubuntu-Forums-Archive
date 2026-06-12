---
title: "How to install Lingo?"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by stb5003 on 2011-06-21
I am trying to install a program called Lingo, from LINDO corporation.  It is a math programming program.  It only downloads as a .tar.gz file, I'm really not sure what to do...

Thanks for any help in advance :)

---

### Post by mikenev on 2011-06-21
You can decompress the file by typing 'tar xzf FILENAME.tar.gz' . That will normally decompress to a folder and you'll find some more instructions inside that. There should be a README file to tell you what to do next.

---

### Post by stb5003 on 2011-06-21
The readme instructions don't make much sense....seem to be geared more towards a command prompt system

---

### Post by jerrrys on 2011-06-21
just double click on it

---

### Post by dFlyer on 2011-06-21
> **stb5003 said:**
> I am trying to install a program called Lingo, from LINDO corporation.  It is a math programming program.  It only downloads as a .tar.gz file, I'm really not sure what to do...

Thanks for any help in advance :)

Right click on the file and select extract. That will extract the file. It may be a program or can be the source code that has to be compiled.

---

### Post by stb5003 on 2011-06-21
It comes with the source file, not an executable file....what do i do with the source file?

---

### Post by jerrrys on 2011-06-21
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+compile+source+code&as_qdr=all&sa=Google+Search&lang=en#956](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+compile+source+code&as_qdr=all&sa=Google+Search&lang=en#956)

---

### Post by snowpine on 2011-06-21
> **stb5003 said:**
> The readme instructions don't make much sense....seem to be geared more towards a command prompt system

If you copy & paste the instructions we can help walk you through them...

---

### Post by jtarin on 2011-06-21
> **snowpine said:**
> If you copy & paste the instructions we can help walk you through them...Or at least give the url of the download site.

---

### Post by stb5003 on 2011-06-21
[FONT=Courier New, monospace][SIZE=2]**2.2. Unix/Linux Platforms:** Follow the steps below to complete the installation:[/SIZE][/FONT]
  

  [FONT=Courier New, monospace][SIZE=2]**Step 1.** For 32-bit Linux platforms, locate the:[/SIZE][/FONT]
  

      [FONT=Courier New, monospace][SIZE=2]LINGO-LINUX-IA32-12.0.tar.gz [/SIZE][/FONT] 
  

  [FONT=Courier New, monospace][SIZE=2]file on your CD.  Alternatively, if you are running a 64-bit version of Linux, then you can choose to install a 64-bit version of LINGO using:[/SIZE][/FONT]
  

      [FONT=Courier New, monospace][SIZE=2]LINGO-LINUX-64x86-12.0.tar.gz[/SIZE][/FONT]
  

 [FONT=Courier New, monospace][SIZE=2]**Step 2.** Copy this file into an installation directory of your choice (e.g. $HOME):[/SIZE][/FONT]
 

     [FONT=Courier New, monospace][SIZE=2]%> cp LINGO-LINUX-IA32-12.0.tar.gz $HOME[/SIZE][/FONT]
 

 [FONT=Courier New, monospace][SIZE=2]**Step 3.** Change the working directory to $HOME and uncompress the file using [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]the ‘gzip –d’ command as below. This operation creates LINGO-LINUX-IA32-12.0.tar (in the case of 64-bit versions, LINGO-LINUX-64x86-12.0.tar will be created).[/SIZE][/FONT]
 

     [FONT=Courier New, monospace][SIZE=2]%> gzip LAPI-LINUX-IA32-12.0.tar.gz[/SIZE][/FONT]
      
 [FONT=Courier New, monospace][SIZE=2]**Step 4.**  Uncompress the tar file using the ‘tar –xvf’ command as below. This will create the LINGO directory lingo12/.[/SIZE][/FONT]
 

     [FONT=Courier New, monospace][SIZE=2]%> tar –xvf LINGO-LINUX-IA32-12.0.tar[/SIZE][/FONT]
 

  [FONT=Courier New, monospace][SIZE=2]**Step 5.** Go to the lingo12/bin/<*PLATFORM*> binaries directory and make sure all the files are in executable mode.  If they are not, you should change their mode by typing[/SIZE][/FONT]
  

      [FONT=Courier New, monospace][SIZE=2]%> chmod 755 *[/SIZE][/FONT]
  

  [FONT=Courier New, monospace][SIZE=2]For 32-bit installations, the <*PLATFORM*> folder will be linux32/ and for 64-bit installations the folder will be linux64/.[/SIZE][/FONT]
 

  [FONT=Courier New, monospace][SIZE=2]**Step 6.** Update the LD_LIBRARY_PATH environment variable so that it also points to the LINGO binaries folder. It is assumed that the installation directory is $HOME/lingo12.[/SIZE][/FONT]
  

      [FONT=Courier New, monospace][SIZE=2]%> LD_LIBRARY_PATH=$HOME/lingo12/bin/*<PLATFORM>*:$LD_LIBRARY_PATH[/SIZE][/FONT]
      [FONT=Courier New, monospace][SIZE=2]%> export LD_LIBRARY_PATH[/SIZE][/FONT]
  

  [FONT=Courier New, monospace][SIZE=2]**Step 7.** Set the LINGO_12_HOME environment variable to point to the main LINGO folder.  For example, if your installation directory is $HOME/lingo12, then the environment variable should be set as: [/SIZE][/FONT] 
  

      [FONT=Courier New, monospace][SIZE=2]%> LINGO_12_HOME=$HOME/lingo12[/SIZE][/FONT]
      [FONT=Courier New, monospace][SIZE=2]%> export LINGO_12_HOME[/SIZE][/FONT]
  

  [FONT=Courier New, monospace][SIZE=2]You may also execute the shell script lingo12/bin/*<PLATFORM>*/lingovars.sh to perform the required updates on these environment variables.  To execute this script manually, enter the following at command line[/SIZE][/FONT]
  [FONT=Courier New, monospace][SIZE=2]	[/SIZE][/FONT]
      [FONT=Courier New, monospace][SIZE=2]%> source $HOME/lingo12/bin/*<PLATFORM>*/lingovars.sh[/SIZE][/FONT]
  

  [FONT=Courier New, monospace][SIZE=2]Alternatively, to execute the script automatically at logon, append this line to the end of your startup script (.bashrc or .bash_profile for the bash shell).[/SIZE][/FONT]
  

  [FONT=Courier New, monospace][SIZE=2]**Step 8.** If you were provided a LINGO license file (look for a file called lndlng12.lic), then you should copy this file into the appropriate folder, e.g.: $HOME/lingo12/license/*<PLATFORM>*.  [/SIZE][/FONT] 
  

  [FONT=Courier New, monospace][SIZE=2]If you do not have a valid LINGO license file and you wish to create a demo license, then go to the lingo12 folder and run the create_demo_license script as follows:[/SIZE][/FONT]
  

          [FONT=Courier New, monospace][SIZE=2]cd $HOME/lingo12[/SIZE][/FONT]
          [FONT=Courier New, monospace][SIZE=2]sh create_demo_license.sh[/SIZE][/FONT]
  

  [FONT=Courier New, monospace][SIZE=2]A demo version of LINGO will run just as standard versions do, however, the maximum model capacity is restricted.[/SIZE][/FONT]
  

  [FONT=Courier New, monospace][SIZE=2]**Step 9.** You should now be able to run LINGO by entering 'lingo12' to a command prompt.  64-bit users should enter 'lingo64_12'. If the environment variables are not set up correctly, you will receive the following error message every time you start LINGO.[/SIZE][/FONT]
  

         [FONT=Courier New, monospace][SIZE=2][Error Code: 171][/SIZE][/FONT]
         [FONT=Courier New, monospace][SIZE=2]License key was not found or is invalid.[/SIZE][/FONT]
  

  [FONT=Courier New, monospace][SIZE=2]In this case, please refer to the steps above to be sure the required environment variables are set up correctly and that you have run the script to create a demo license.[/SIZE][/FONT]

---

### Post by snowpine on 2011-06-21
I have to be honest, those instructions are a little over my head... definitely not the usual make/make install I'm used to. :( Does Lingo have any tech support you can use (since it is a commercial product)?

---

### Post by jtarin on 2011-06-21
Let's try to make this easy:
1.You will need to do this from the command line and you should have the downloaded file into your 
**/home/username directory**.

2.In your terminal as a user you will automatically be in your **/home/username directory**. Enter the command ```
ls
``` and this will list all your directories and files under /home/username directory. Verify that the file is listed.
If not you do not have the file in the correct location or you are not in your /home/username directory.
If it is there then you can proceed. If not come back to the forum and ask for help.

3.Now enter the command ```
gzip LAPI-LINUX-IA32-12.0.tar.gz
``` (or the correct file name if it is different. After that command you can use the command "ls" again to verify 
the unzipped tar file is there. You should see something like "LINGO-LINUX-IA32-12.0.tar". If it is there then 
you can proceed. If not come back to the forum and ask for help.

4.Uncompress the tar file using the ‘tar –xvf’ command as below. This will create the LINGO directory lingo12/. ```
tar –xvf LINGO-LINUX-IA32-12.0.tar
```

5.Now in the terminal again issue the command "ls". You should see a directory named lingo12. If it is there then you 
can proceed. If not come back to the forum and ask for help.

6.In the terminal type ```
cd lingo12/bin/<PLATFORM>
``` this will place you in the /<PLATFORM>  directory. (For 32-bit installations, the <PLATFORM> folder will be linux32/ and 
for 64-bit installations the folder will be linux64/). 
If it is there then you can proceed. If not come back to the forum and ask for help.

7.Now while you are in the /<PLATFORM> directory you will make all the files executable by issuing the command ```
chmod 755 *
```

8. Now in the terminal type ```
LD_LIBRARY_PATH=$HOME/lingo12/bin/<PLATFORM>:$LD_LIBRARY_PATH
```
then next the command ```
export LD_LIBRARY_PATH
```

9. Next in the terminal type ```
LINGO_12_HOME=$HOME/lingo12
``` then the next command will be ```
export LINGO_12_HOME
```.

10. You should still be in the /lingo12/bin/<PLATFORM> directory run the command "ls" again and look for a file 
named "lingovars.sh". If it is there then you can proceed. If not come back to the forum and ask for help.

11.You may also execute the shell script lingo12/bin/<PLATFORM>/lingovars.sh to perform the required updates on 
these environment variables. To execute this script manually, enter the following at command line.

```
source $HOME/lingo12/bin/<PLATFORM>/lingovars.sh
```

If it runs..OK....if problems stop and come back to the forum.


The rest of the steps I think you can do. At any point something is not right STOP, DO NOT CLOSE TERMINAL 
and come ask in the forum. After every command I have listed it goes without saying you should press the "Enter" for the command to execute. Good Luck

Someone might look over my instructions to see if anything is amiss.

---

