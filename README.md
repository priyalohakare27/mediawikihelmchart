# MediawikiHelmchart
This project is used to deploy the mediawiki, using HELM charts

Mediawiki Implementation using HELM Charts

**Prerequisites:**
- AWS account with access keys and secret access key generated for same
- kubectl  installed onto machine
- Helm installed
- AWS RDS for MariaDB

Steps:
1.	I have deployed the EKS on my account. When you do kubectl get nodes, you get the following output.

 ![image](https://user-images.githubusercontent.com/25103050/116522744-2834cb80-a8f3-11eb-973e-91766447dbd7.png)


2.	Now, clone the project, and do:
helm install mediwiki-app mediawikipriya/ --values mediawikichart/values.yaml
3.	It will deploy the Mediawiki app. You can access through the External-IP
 ![image](https://user-images.githubusercontent.com/25103050/116522781-31be3380-a8f3-11eb-9ccb-5bc838b60bed.png)


4.	When you hit the external-ip on the browser, you get the below installation page.
5.	Press continue for DB setup

![image](https://user-images.githubusercontent.com/25103050/116522799-371b7e00-a8f3-11eb-812d-c2c9d71fea11.png)

 


6.	Use AWS RDS DB crederntials provided in apply output for setup
7.	Confirm database setting and continue
![image](https://user-images.githubusercontent.com/25103050/116522819-3b479b80-a8f3-11eb-9e8b-095a30c4d1a7.png)

 
8.	Configure details for wiki namespace
9.	Confirm the installation and continue
10.	Next page will show the status of all tasks done


![image](https://user-images.githubusercontent.com/25103050/116522848-40a4e600-a8f3-11eb-803c-5eb7eabb4848.png)




 11.	Below page provides the LocalSettings.php file which will get downloaded on browser
	![image](https://user-images.githubusercontent.com/25103050/116522888-4995b780-a8f3-11eb-9927-7579dd7b73d0.png)

 
12.	Ones you have the file on browser needs to copy the file into the EC2 instance at location `/var/www/html/mediawiki` for which you need to ssh onto server using the key which you have generated for EC2
13.	We can mount LocalSettings.php to containers using volumes. We have to use Persistent Volume and Persistent Volume Claim feature for this. For EKS multi node cluster, we can use AWS EFS as Persistent Volume for better Read/Write operations of PHP Application. 
14.	Ones copied click onto `enter your wiki` link available onto page where php file is downloaded you will be redirected to your wiki

![image](https://user-images.githubusercontent.com/25103050/116522922-51edf280-a8f3-11eb-9579-58f9c46146b4.png)

 

