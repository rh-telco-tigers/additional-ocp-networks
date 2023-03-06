The Openshift documentation describes many different methods to add additional networks to your cluster.  There are lots of options and sometimes these options overlap (many different ways to accomplish same task) and other times, only one method of adding the additional network may be supported based on the type of networking hardware (SR-IOV card is one example) that is being used.

When deciding which method to use, a question you may need to ask yourself is whether the additional networks are only needed for internal communication between two workloads (IE: pods) or if the additional network needs to expose an application to be reachable outside of the cluster.  In the latter-case, exposing the workload can happen via another ingress/route (internal load balancer), a NodePort, external IP resource, or using the MetalLB Operator.

Additional networks can mean defining an additional VLAN on the primary NIC card on a control-plane node (not a common use-case) or using additional NIC cards on the control plane/worker nodes (including SR-IOV cards).  These different NIC cards/networks may have varying characteristics including throughput requirements (1Gbps/10Gbps/etc) and may need to be segmented from other networks (IE: control-plane/upstream/Internet) due to security needs.

https://www.myopenshiftblog.com/additional-ocp-networks/
