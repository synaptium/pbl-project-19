AUTOMATE INFRASTRUCTURE WITH IAC USING TERRAFORM PART 4

Create a terraform cloud account. Verify it via email and create an organization, creeate a workspace, connect gitlab and set enviromet variables by adding aws access and secret keys

![alt text](./tcloud.png)

Install packer and choco

Use acker to build all 4 amis

![alt text](./amis.png)

I went to ami folder

Rank packer for each packer file and build the AMIs

Go to davids gitlab and fork his terrform repo and clone it to my pc via vscode.

Do same with his ansible repo.

![alt text](./clone.png)

Copy the ami ids for all 4 amis and replace them in the terraform.auto.tfvars file


![alt text](./tfvars.png)

Also replace the pem key and aws acc number

Push everything to gitalb

Now go to terraform cloud and start a run

![alt text](./terraform.png)

I had many errors and corrected all.

![alt text](./terraform2.png)

![alt text](./good.png)

Configure ssh agent

if you are not able to login to ssh within ssh via ssh agent do this

Open gitbash on vscode

run eval `ssh-agent -s`

then ssh-add k pemkey.pemkey

its adds the pem key try again

![alt text](./sshadd.png)

Get the bastion public dns and configure it in vscode to connect via remote host.

![alt text](./publicdns.png)

check if aws cli command is inatsalled via the command aws

it was so clone down the ansible repository

Run aws configure to connect aws account to your bastion server.

Make sure ssh agent is working. type ssh-add -l

change dir to ansible folder.

Run ansible-playbook -i inventory/aws_ec2.yml playbooks/site.yml --graph

Did not work

So i had to install pyhton 3.8, boto, botocore and pip3

sudo yum install -y python38
 sudo python3.8 -m pip install boto3 botocore

 You can install pip using this link

 https://shouts.dev/articles/install-pip3-or-pip2-on-rhel-centos8

 It worked now after running this.

 ansible-playbook -i inventory/aws_ec2.yml playbooks/site.yml --graph

G to aws and copy the dns name for the load balancer.

![alt text](./load.png)

![alt text](./nginx.png)

 Go to rds and copy the endpoints







Now i logged in to the bastion server via ssh, then entered nginx via ssh agent









