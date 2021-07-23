# Tagging objects in a bucket in Amazon Lightsail<a name="amazon-lightsail-tagging-bucket-objects"></a>

 *Last updated: July 14, 2021* 

Tag objects in your bucket to categorize them by purpose, owner, environment, or other criteria\. Tags can be added to objects when you upload them, or after they are uploaded\. For more information about buckets, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\.

## Add and delete tags for objects using the Lightsail console<a name="add-delete-object-tags-lightsail-console"></a>

Complete the following procedure to add or delete tags from objects in a bucket using the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Storage** tab\.

1. Choose the name of the bucket for which you want to tag objects\.

1. Use the **Objects browser** pane in the **Objects** tab to browse to the location of the object\.

1. Add a checkmark next to the object for which you want to add or delete a tag\.

1. In the object information pane, choose one of the following options under the **Object tags** section:
   + **Add** or **Edit** \(if tags have already been added\)\. Enter a key into the Key text box, and a value into the **Value** text box\. Then, choose **Save** to add the tag\. Otherwise, choose **Cancel**\.
   + **Edit**, and then choose the **X** next to the key\-value tag that you want to delete\. Choose **Save** when you're done to delete the tag, or choose **Cancel** to not delete it\.

## Add and delete tags for objects using the AWS CLI<a name="add-delete-object-tags-aws-cli"></a>

Complete the following procedure to add tags to objects or delete tags from objects using the AWS Command Line Interface \(AWS CLI\)\. You do this by using the `put-object-tagging` and `delete-object-tagging` commands\. For more information, see [put\-object\-tagging](https://docs.aws.amazon.com/cli/latest/reference/s3api/put-object-tagging.html) and [delete\-object\-tagging](https://docs.aws.amazon.com/cli/latest/reference/s3api/delete-object-tagging.html) in the *AWS CLI Command Reference*\.

**Note**  
You must install the AWS CLI and configure it for Lightsail and Amazon S3 before continuing with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window\.

1. Enter one of the following commands:
   + To add a tag to an object:

     ```
     aws s3api put-object-tagging --bucket BucketName --key ObjectKey --tagging "{\"TagSet\":[{ \"Key\": \"KeyTag\", \"Value\": \"ValueTag\" }]}"
     ```

     In the command, replace the following example text with your own:
     + *BucketName* \- The name of the bucket that contains the object you want to tag\.
     + *ObjectKey* \- The full object key of the object you want to tag\.
     + *KeyTag* \- The key value of your tag\.
     + *ValueTag* \- The value of your tag\.
   + To add a tag to an object:

     ```
     aws s3api put-object-tagging --bucket BucketName --key ObjectKey --tagging "{\"TagSet\":[{ \"Key\": \"KeyTag1\", \"Value\": \"ValueTag1\" }, { \"Key\": \"KeyTag2\", \"Value\": \"ValueTag2\" }]}"
     ```

     In the command, replace the following example text with your own:
     + *BucketName* \- The name of the bucket that contains the object you want to tag\.
     + *ObjectKey* \- The full object key of the object you want to tag\.
     + *KeyTag1* \- The key value of your first tag\.
     + *ValueTag1* \- The value of your first tag\.
     + *KeyTag2* \- The key value of your second tag\.
     + *ValueTag2* \- The value of your second tag\.
   + To delete all tags from an object:

     ```
     aws s3api delete-object-tagging --bucket BucketName --key ObjectKey
     ```

     In the command, replace the following example text with your own:
     + *BucketName* \- The name of the bucket that contains the object for which you want to delete all tags\.
     + *ObjectKey* \- The full object key of the object you want to tag\.

   Example:

   ```
   aws s3api delete-object --bucket DOC-EXAMPLE-BUCKET --key nptLmg6jqDo.jpg --tagging "{\"TagSet\":[{ \"Key\": \"Importance\", \"Value\": \"High\" }]}"
   ```

   You should see a result similar to the following example:  
![\[Result of the AWS CLI put-object-tagging command\]](https://d9yljz1nd5001.cloudfront.net/en_us/cdafd3c2a6d9edfefee89eda217b0068/images/amazon-lightsail-s3api-put-object-tagging-result.png)

## Managing buckets and objects in Lightsail<a name="tagging-objects-managing-buckets-and-objects"></a>

These are the general steps to manage your Lightsail object storage bucket:

1. Learn about objects and buckets in the Amazon Lightsail object storage service\. For more information, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\.

1. Learn about the names that you can give your buckets in Amazon Lightsail\. For more information, see [Bucket naming rules in Amazon Lightsail](bucket-naming-rules-in-amazon-lightsail.md)\.

1. Get started with the Lightsail object storage service by creating a bucket\. For more information, see [Creating buckets in Amazon Lightsail](amazon-lightsail-creating-buckets.md)\.

1. Learn about the access permissions that you can configure for your bucket\. You can make all objects in your bucket public or private, or you can choose to make individual objects public\. You can also grant access to your bucket by creating access keys, attaching instances to your bucket, and granting access to other AWS accounts\. For more information, see [Understanding bucket permissions in Amazon Lightsail](amazon-lightsail-understanding-bucket-permissions.md)\.

   After learning about bucket access permissions, see the following guides to grant access to your bucket:
   + [Configuring bucket access permissions in Amazon Lightsail](amazon-lightsail-configuring-bucket-permissions.md)
   + [Configuring access permissions for individual objects in a bucket in Amazon Lightsail](amazon-lightsail-configuring-individual-object-access.md)
   + [Creating access keys for a bucket in Amazon Lightsail](amazon-lightsail-creating-bucket-access-keys.md)
   + [Configuring resource access for a bucket in Amazon Lightsail](amazon-lightsail-configuring-bucket-resource-access.md)
   + [Configuring cross\-account access for a bucket in Amazon Lightsail](amazon-lightsail-configuring-bucket-cross-account-access.md)

1. Create an IAM policy that grants a user the ability to manage a bucket in Lightsail\. For more information, see [IAM policy to manage buckets in Amazon Lightsail](amazon-lightsail-bucket-management-policies.md)\.

1. Learn about the way that objects in your bucket are labeled and identified\. For more information, see [Understanding object key names in Amazon Lightsail](understanding-bucket-object-key-names-in-amazon-lightsail.md)\.

1. Learn how to upload files and manage objects in your buckets\. For more information, see the following guides\.
   + [Uploading files to a bucket in Amazon Lightsail](amazon-lightsail-uploading-files-to-a-bucket.md)
   + [Uploading files to a bucket in Amazon Lightsail using multipart upload](amazon-lightsail-uploading-files-to-a-bucket-using-multipart-upload.md)
   + [Viewing objects in a bucket in Amazon Lightsail](amazon-lightsail-viewing-objects-in-a-bucket.md)
   + [Copying or moving objects in a bucket in Amazon Lightsail](amazon-lightsail-copying-moving-bucket-objects.md)
   + [Downloading objects from a bucket in Amazon Lightsail](amazon-lightsail-downloading-bucket-objects.md)
   + [Filtering objects in a bucket in Amazon Lightsail](amazon-lightsail-filtering-bucket-objects.md)
   + [Tagging objects in a bucket in Amazon Lightsail](#amazon-lightsail-tagging-bucket-objects)
   + [Deleting objects in a bucket in Amazon Lightsail](amazon-lightsail-deleting-bucket-objects.md)

1. Enable object versioning to preserve, retrieve, and restore every version of every object stored in your bucket\. For more information, see [Enabling and suspending object versioning in a bucket in Amazon Lightsail](amazon-lightsail-managing-bucket-object-versioning.md)\.

1. After enabling object versioning, you can restore previous versions of objects in your bucket\. For more information, see [Restoring previous versions of objects in a bucket in Amazon Lightsail](amazon-lightsail-restoring-bucket-object-versions.md)\.

1. Monitor the utilization of your bucket\. For more information, see [Viewing metrics for your bucket in Amazon Lightsail](amazon-lightsail-viewing-bucket-metrics.md)\.

1. Configure an alarm for bucket metrics to be notified when the utilization of your bucket crosses a threshold\. For more information, see [Creating bucket metric alarms in Amazon Lightsail](amazon-lightsail-adding-bucket-metric-alarms.md)\.

1. Change the storage plan of your bucket if it's running low on storage and network transfer\. For more information, see [Changing the plan of your bucket in Amazon Lightsail](amazon-lightsail-changing-bucket-plans.md)\.

1. Learn how to connect your bucket to other resources\. For more information, see the following tutorials\.
   + [Tutorial: Connecting a WordPress instance to an Amazon Lightsail bucket](amazon-lightsail-connecting-buckets-to-wordpress.md)
   + [Tutorial: Using an Amazon Lightsail bucket with a Lightsail content delivery network distribution](amazon-lightsail-using-distributions-with-buckets.md)

1. Delete your bucket if you're no longer using it\. For more information, see [Deleting buckets in Amazon Lightsail](amazon-lightsail-deleting-buckets.md)\.