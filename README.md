# Let's encrypt SSL-Activation for Bitnami Certbot method

1.Certbot is not available in the default ubuntu repository. Run the below command to add ppa repository.<br>
<br>
<code> sudo add-apt-repository ppa:certbot/certbot </code> <br>
<br>
2. Update packages using below command. <br>
<br>
<code> sudo apt update </code> <br>
<br>
3. Run below command to install certbot <br>
<br>
<code> sudo apt install certbot </code> <br>
<br>
4. Activate Domain and Wildcard generation <br>
<br>
<code> $ sudo certbot certonly --manual -d *.example.com -d example.com --agree-tos --no-bootstrap --manual-public-ip-logging-ok --preferred-challenges dns-01 --server https://acme-v02.api.letsencrypt.org/directory </code> <br>
<br>
5.In these above command running , you have to verify DNS TXT in records for acme challenge and wait for TTL  <br>
<br>
6. After See "Congratualtion Message". copy ssl certfile location. <br>
<br>
7. Now create or edit the Virtual host for configuration. <br>
<br>
<code> sudo nano /opt/bitnami/apps/wordpress/conf/httpd-vhosts.conf </code> <br>
<br>
Change the server name and alias. and configure path of certfile location.<br>
<br>
8.Change Bitnami Vhost into the file. <br>
<br>
 <code> sudo nano /opt/bitnami/apache2/conf/bitnami/bitnami-apps-vhosts.conf </code> <br>
 <br>
 adding this line on bottom <br>
 <br>
 <code> Include "/opt/bitnami/apps/wordpress/conf/httpd-vhosts.conf" </code> <br>
 <br>
 9. Restart apache server.<br>
 <br>
 <code> sudo /opt/bitnami/ctlscript.sh restart apache </code><br>
  <br>
  10. If you didn't see any error's that's it. 
  <br>
    <br>
      <br>
        <br>
        
  <h3> Fixing Can't connect error's </h3><br>
  <br>
  * Type Your Instance IP and it would shows Apache default webpage.  <br>
  <br>
  <code> sudo systemctl disable apache2 </code><br>
  <br>
  * Reboot Instance <br>
  <br>
  <b> Now Your Site is working ! </b>
  

