# cpanel-change-document-root
Change Primary Domain Document Root in Cpanel


Step to Change Document Root
First of all access your server via SSH as Root Server or WHM terminal both have the same process to change Document root. If you want to use any ssh client you can download “Putty” software to access the server.

WHM Panel

2. At this time our main document root is public_html and our requirement is to change this to public_html/public. This requirement change be vary as per your requirement.


Cpanel Document root by default

3. now we write our first command to access our domain configuration file with vim. If you don’t know to use vim don’t worry i will tell you how you can edit and save your file. just try the command is written below by replacing domain.com to yourdomain name and yourusername to your current username

nano /var/cpanel/userdata/yourusername/domain.com

4. now change your document path as we changed into current editing file.

5. after finish editing you need to save your file.  To save file in nano you need to press CTRL+X button then press y after that you press enter.

6. now same done on SSL file if your site is SSL enabled. If you are not using SSL then you can skip this one.

nano/var/cpanel/userdata/yourusername/domain.com_SSL

7. now change your document path as we changed into current editing file.


domain ssl config file

8. after finish editing you need to save your file. To save file in nano you need to press CTRL+X button then press y after that you press enter.

9. Now to need to delete cache of main domain or ssl. To do it you need to run two commands.


remove cache file from server config file

rm -vf /var/cpanel/userdata/yourusername/domain.com.cache
&&
rm -vf /var/cpanel/userdata/yourusername/domain.com_SSL.cache

10. Now you need to update your userdatacache and build httpd config. To do this again you need to run two more commands

/scripts/updateuserdatacache

/scripts/rebuildhttpdconf


11. Now all set. You just need one more command to restart your server.

service httpd restart

12. Now you can check your cpanel main or primary domain document path is changed.

