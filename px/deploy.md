# couple git related
git reset --hard HEAD  (discard local changes not commited)
git reset --hard origin/main   (discard local changes even commited locally, not to remote yet)

git rm -r --cached .env

git add .
git commit -m 'your message'
git push

##
https://github.com/petermyqops/copilot-metrics-viewer

npm install
npm run serve

## copy & paste ACCESS KEY ID and SECRET ACCESS KEY
cd /Users/pxu/CODE/Copliot/JS/copilot-metrics-viewer

log in to TEND AWS Cloud, ECS Cluster (devCluster-fargate)


##

docker build -t copilot-metrics-viewer .
docker run -p 8080:80 copilot-metrics-viewer


## push docker image to AWS 
aws s3 ls

aws ecr create-repository --repository-name copilot-metrics-viewer  --image-scanning-configuration scanOnPush=true --region us-east-1

docker tag copilot-metrics-viewer:latest 211125524049.dkr.ecr.us-east-1.amazonaws.com/copilot-metrics-viewer

aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 211125524049.dkr.ecr.us-east-1.amazonaws.com

docker push 211125524049.dkr.ecr.us-east-1.amazonaws.com/copilot-metrics-viewer

## restart task and find new public IP
http://3.238.1.35/
