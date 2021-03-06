# spark-yarn-jupyter-kubernetes
Spark2.0 Cluster on Yarn with Jupyter Notebook - with Kubernetes 

This is a kubernetes script to create the spark 2.0  cluster on Google Cloud Platform.

Prerequiste: 
  1. Have gcloud and kubernetes install and configure.
  
      `git clone https://github.com/senthilaru/spark-yarn-jupyter-kubernetes`
      
     `cd spark-yarn-jupyter-kubernetes`
     
  2. Create an external IP(EXTERNAL_IP) in Google Cloud (https://console.cloud.google.com/networking/addresses/list) and place the IP in the file (spark_lb_service.yaml) by replacing the IP(146.148.111.138) exists in the last line.
    
       `kubectl create -f  spark-yarn-jupyter-kubernetes/`
       
  3. Wait for sometime, till the GC creates the spark cluster. You can check it out using below URL.
  
      `Jupyter Notebook - http://EXTERNAL_IP:8888`
      
      `Spark - http://EXTERNAL_IP:8080`
      
     ` Yarn - http://EXTERNAL_IP:8088`
     
  4. Cluster size will be 2 (1 - Master node and 1 Worker node). If you want to increase the cluster size, change it in the file (worker_deploy.yaml) spec:replicas: 1
  
  5. Autoscale spark workers by running the below command
  
      `kubectl autoscale deployment worker --cpu-percent=75 --min=1 --max=10`
      
  6. Finally to delete all
        `kubectl delete -f  spark-yarn-jupyter-kubernetes/`
  
