---
title: "help formating rkhunter results"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by jba6511 on 2008-12-27
I have written a perl script that calls chkrootkit and rkhunter. The results are then written to a file and emailed to me. However, I can not get the results from rkhunter to appear correctly in thunderbird. Here is what I mean:

[PHP][0;35mChecking application versions...[0;39m

    Checking version of Exim MTA[29C[ [0;32mOK[0;39m ]
    Checking version of GnuPG[32C[ [0;32mOK[0;39m ]
    Checking version of OpenSSL[30C[ [0;32mOK[0;39m ][/PHP]

I have tried adding html tags but that does not help. The formatting appears correct in my results.txt file, just not in thunderbird. Any ideas?

The following is what I am using and I am by no means claiming to be proficient with programming in perl.

[PHP]#!/usr/bin/perl
# this script:
# 1. runs chkroot and rkhunter
# 2. writes the results to temp files in the /tmp directory
# 3. uses mail (exim4) to email the results to gmail account
# 4. deletes the temp files in /tmp
# note: this script has to be run as root in order to execute chkrootkit and rkhunter

# call to run chkrootkit
chkrootkit();

# call to run rkhunter
rkhunter();

# call to open the results file 
openfile();

# call to mail the results
mail();

# call to remove tmp files
housekeeping();

#--------subroutines-------

sub chkrootkit {

	# runs chkrootkit and writes results to the file chkrootkitresults.txt in the /tmp directory
	my $chkrootkitcall = "chkrootkit > /tmp/chkrootkitresults.txt";
	system ("$chkrootkitcall");

}

sub rkhunter {

	# runs rkhunter and writes results to the file rkhunterresults.txt in the /tmp directory
	my $rkhuntercall = "rkhunter --update && sudo rkhunter -c -sk > /tmp/rkhunterresults.txt";
	system ("$rkhuntercall");

}

sub openfile {
	
	# creates the file to hold the results of chkrootkit and rkhunter
	open (RESULTS, ">/tmp/results.txt") || die ("Could not create results.txt file in /tmp");

	# reads in chkrootkitresults.txt and rkhunterresults.txt
	open (CHKRESULTS, "/tmp/chkrootkitresults.txt") || die ("Could not open /tmp/chkrootkitresults.txt");
	my @chkrootkit_array = <CHKRESULTS>;
	close (CHKRESULTS);

	open (RKRESULTS, "/tmp/rkhunterresults.txt") || die ("Could not open /tmp/rkhunterresults.txt");
	my @rkhunter_array = <RKRESULTS>;
	close (RKRESULTS);

	# prints contents to file
	print RESULTS ("<html>");
	print RESULTS ("Results from chkrootkit:\n");
	print RESULTS (@chkrootkit_array);
	print RESULTS ("\nResults from rkhunter:\n");
	print RESULTS (@rkhunter_array);
	print RESULTS ("</html>");

	# close results file
	close (RESULTS);

}

sub mail {

	# mail the results file to gmail account
	my $mailcall = "/usr/bin/mail -s \"Rootkit Detection Results\" removed\@gmail.com < /tmp/results.txt";
	system ("$mailcall");	

}

sub housekeeping {

	# delete tmp files 
	my $cleanupcall = "rm -f /tmp/chkrootkitresults.txt /tmp/rkhunterresults.txt /tmp/results.txt";
	system ("$cleanupcall");

}
[/PHP]

---

