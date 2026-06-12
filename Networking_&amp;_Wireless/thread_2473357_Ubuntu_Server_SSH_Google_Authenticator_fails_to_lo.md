---
title: "Ubuntu Server SSH Google Authenticator fails to log in, repeats asking for passwords"
date: 2022-04-01
forum: Networking &amp; Wireless
---

### Post by vladi443 on 2022-04-01
Hello Everyone,

I am quite new with Ubuntu, I've been messing around with some Desktop Ubuntu computers together with some Ubuntu servers. Recently I decided to use one of my old laptops and turn it into an Ubuntu server to experiment on it. Reading articles about hardening Ubuntu SSH I found the google authenticator program so I decided to give it a try, I followed multiple guides but neither was successful and I even got locked out accidentally in the middle of it. Here is what I have so far:

I logged in my profile (example: *user1) *and executed ***sudo apt-get install libpam-google-authenticator. ***Everything went smoothly and the google authenticator downloaded successfully.
After that I typed in ***google-authenticator ***which generated the QR code and the different codes. After that I was prompted with the questions about its setup, and I answered *yes*to all of them.

Then I added ***auth required pam_google_authenticator.so nullok*** to  ***/etc/pam.d/sshd ***and ***ChallengeResponseAuthentication yes*** to ***/etc/ssh/sshd_config*** (*note: I did check both files for duplicates to make sure they are not overriding, but there were none*).

After that was completed, I executed *** systemctl restart sshd.service*** *(note: I also trying executing service ssh restart and rebooting my whole system*).

Once I completed these steps, I downloaded the Google Authenticator Code and added a new profile, with the account name being *user1* and the key being the *security key* provided when running the ***google-authenticator ***command.

I was then prompted with the 6-digit passcode by the Google Authenticator that I had to enter together with my normal password login. However, that is where it gets messy.
When I tried to SSH into my machine from a different machine (u*sing my Mac's terminal*) I typed ***ssh [EMAIL="user1@ip.addres"]user1@ip.addres[/EMAIL]s.0.0 ***and I was prompted to enter my user's password. Entering that password works fine, however then I am prompted with the console saying *_AUTHENTICATION KEY_*, for which I logged into the Google app and used the code provided there. Upon entering however, the console just kicks me back to asking for my *password* which once entered asks for the _*AUTHENTICATION KEY*_ and this keeps on repeating until I reach the maximum login attempts I've set (*&#8203;I increased it to 6 to troubleshoot*).

I tried researching and reading different guides, but no matter what I did I always end up with the same problem. I even tried SSH-ing from the server itself by typing ***user1@localhost ***but the same thing happened.

If any of you have any suggestions or ideas or would like me to share more info (*like **logs, guides I looked at, etc.*) let me know. I would really want to make it work as I think it provides excellent security and of course looks cool :P. Any help would be greatly appreciated!

Thank you again for taking the time to read this, I apologize if the formatting looks odd, I just made my account so I am still not really sure how to properly quote and format commands, paths, etc.

Thank you again guys!

---

### Post by vladi443 on 2022-04-02
Hello again,

After some time messing around with the Google Authenticator and reading different guides and articles I figured out the problem. When I setup my Linux server, it defaulted to *UTC* time, which is different than my time zone. This resulted in the server to not match my local time, and thus not validate the OTP.

I updated my server's time zone by executing ***timedatectl set-timezone Time/Zone*** and then ran the ***google-authenticator*** command again to re-setup the authenticator. After that I restarted SSH by running ***service ssh restart***, added the new codes into the *Google Authenticator* app and then I was able to login through SSH successfully.

I know this question was very specific but I was just really confused about it. Hopefully if anyone else encounters that (and is new like me:o) this will help.

Thank you guys!

---

