---
title: "Daemon not forkring child process (message dialog) on optimized"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by alibaba163 on 2009-05-16
Hi Guys,
        I am stuck with very strange problem. I have developed a daemon on ubuntu 8.10. This daemon is written in C using kdevelop (as IDE).

This daemon launches itself on system boot and connects to Gateway on Windows operating system. The work of daemon is very simple it just forks a child process whenever request is send from gateway on windows.

On Forking the process, deamon simply launches a dialog build in gtkmm using kdevelop. The dialg( a notification) reside at /usr/nsn/gui/message/.

Daemon performs differently with debug and release mode

ON RELEASE MODE (OPTIMIZED MODE):

The problem is that daemon works absolutely fine when I start the daemon from terminal, using following command
         sudo /etc/init.d/notifydaemon (name of daemon is notifydaemon)

  But it does'nt lauch the child process when system is rebooted. Daemon does get started and I can see the daemon in ps aux | grep notifydaemon
but it does not launch the dialog.

All the variable values are fine since I have debugged the code by writing values in log files. however, same daemon performs perfect while running in debug mode

ON DEBUG MODE:

Same daemon works absolutely fine in debug mode. It lauches the dialog on /usr/nsn/gui/message when I start daemon from terminal

Also it launches the dialog when system is rebooted.


Peace of code which launches the dialog is given below

   pid_t ForkGuiProcess(const char * directory, const char * command, char ** putenvs)
    {
        std::string path (directory);
	path += "/";
        path += command;


        pid_t pid = ::fork();
        if(pid == -1)
        {
	  
	nsm::Log ("Couldn't fork UI Process");
            // Horrible error
            return -1;
        } 
        else if(pid != 0)
        {
            return pid;
        }
        else
        {

	  //nsm::Log ("Forked UI process");
 

	    // If root, spoof the current UI user
	    if (::geteuid () == 0)
	    {

            }
            //nsm::Log(::getenv("XAUTHORITY"));
                           //nsm::Log(::getenv("DISPLAY"));
            //nsm::Log(path); 
			
			// Set any environment variables the user wants us to
            if (putenvs != NULL)
            {
                while (*putenvs != NULL)
                {
                    putenv(*putenvs);
                    putenvs++;
                }
            }
			

            // Run the command
            char * args[] = {(char *)path.c_str(), NULL};
            int err = ::execv(path.c_str(), args);
            if (err != 0)
            {
                nsm::Log("Error launching child process");
                std::exit(1);
            }
        }
        return pid; 
    }

}


Please help!!!!!!!!!!!!!!

Thanks.

Sheikh.

---

### Post by Joeb454 on 2009-05-16
Please don't create duplicate threads on the same subject.
Thread closed - original thread here:  [http://ubuntuforums.org/showthread.php?t=1161594](http://ubuntuforums.org/showthread.php?t=1161594)

---

